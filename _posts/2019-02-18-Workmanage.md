---
title: "Workmanager"
date: 2019-02-18 13:43:28 -0400
---

Gradle 추가
implementation "android.arch.work:work-runtime-ktx:$rootProject.workVersion"



Periodic work has a minimum interval of 15 minutes and it cannot have an initial delay.
주기적인 워커는 최소 15분의 간격이 있으면 초기 지연을 가질 수 없다.





private fun optimizeContent() {
        val commonViewModel =  ViewModelProviders.of(this).get(CommonViewModel::class.java)
        val delay = commonViewModel.getWorkManagerDelay()

        val optimizeWorkRequest = OneTimeWorkRequestBuilder<OptimizeContentWorker>()
                .setInitialDelay(delay, TimeUnit.MILLISECONDS)
                .addTag(OPTIMIZE_WORK_NAME)
                .build()

        WorkManager.getInstance()
                .beginUniqueWork(OPTIMIZE_WORK_NAME, ExistingWorkPolicy.KEEP, optimizeWorkRequest)
                .enqueue()

        WorkManager.getInstance()
                .getWorkInfosForUniqueWorkLiveData(OPTIMIZE_WORK_NAME).observe(this, Observer { infos ->
                    if(!infos.isNullOrEmpty()) {
                        for (info in infos) {
                            if (info.state.isFinished) {
                                moveTaskToBack(true)
                            }
                        }
                    }
                })
    }

    private fun uploadPhoto() {
        Log.d("TEST1234", "uploadPhoto")
        val uploadConstraints = Constraints.Builder()
                .setRequiredNetworkType(NetworkType.CONNECTED)
                .setRequiresBatteryNotLow(true)
                .build()

        val uploadWorkRequest = PeriodicWorkRequestBuilder<PhotoUploadWorker>(2, TimeUnit.MINUTES)
//                .setConstraints(uploadConstraints)
                .build()

        WorkManager.getInstance()
                .enqueueUniquePeriodicWork(PHOTO_UPLOADER_WORK_NAME, ExistingPeriodicWorkPolicy.KEEP, uploadWorkRequest)
    }
    
    
    
class OptimizeContentWorker(context: Context, workerParams: WorkerParameters) : Worker(context, workerParams) {

    private val contentList:  MutableSet<String> = mutableSetOf()
    private val mAppExecutors = AppExecutors()

    override fun doWork(): Result {
        getAllContent()

        return Result.success()
    }

    private fun getAllContent() {
        val months = getRepository().getContentMonths()
        val weeks = getRepository().getContentWeeks()

        for(month in months.iterator()) {
            contentList.add(month.getMonthImageLocal().path.toString())
        }

        for(week in weeks.iterator()) {
            contentList.add(week.getWeekImageLocal().path.toString())
            contentList.add(week.getIconLocal().path.toString())
            contentList.add(week.getDataLocal().path.toString())
        }

        val savedRoot = SSFileHelper.getPrivateLocalFile("")
        checkAllLocalFile(savedRoot)

    }

    private fun checkAllLocalFile(directory: File) {
        for (file in directory.list()) {
            val filePath = String.format("%s/%s", directory.path, file)
            val localFile = File(filePath)
            if (localFile.isDirectory) {
                if (!file.startsWith(".")) {
                    checkAllLocalFile(localFile)
                }
            }
            else {
                if (!contentList.filter { it == filePath }.any() && !file.endsWith(".json")) {
                    localFile.delete()
                }
            }
        }
    }

    private fun getDatabase(): AppDatabase {
        return AppDatabase.getInstance(applicationContext, mAppExecutors)
    }

    private fun getRepository(): DataRepository {
        return DataRepository.getInstance(getDatabase(), mAppExecutors)
    }
}


class PhotoUploadWorker(context: Context, workerParams: WorkerParameters) : Worker(context, workerParams) {

    private val mAppExecutors = AppExecutors()

    override fun doWork(): Result {
        getRepository().uploadAllPhotos()
//        getAllPhoto()

        return Result.success()
    }

    private fun getDatabase(): AppDatabase {
        return AppDatabase.getInstance(applicationContext, mAppExecutors)
    }

    private fun getRepository(): DataRepository {
        return DataRepository.getInstance(getDatabase(), mAppExecutors)
    }
}

