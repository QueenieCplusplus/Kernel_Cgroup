# Kernel Cgroup

Cgroup 控制群組是將任意 processes 包成群組一并管理的 Kernel 功能，Cgroup 本身是提供程序上群組化功能介面的架構，之後再利用架構實作 I/O 與記憶體配置控制等具體的資源管理功能，這些具體的資源管理功能稱為 Cgroup subsystem 或是 controller。

Cgroup 管理 groups 與設定各 subsystems 的使用者介面，是透過 cgroup “虛擬檔案系統” 提供，使用 Cgroup 的時候，需要先掛載 cgroup 檔案系統，並且可透過掛載選項指定使用哪些 sbsystem。

掛載方式：

    # mount -t cgoup -o debug cgroup /cgoup


確認方式：

    /proc/cgroups
    
掛載後，確認掛載點下有哪些檔案：

    #ls /cgroup
    
    cgroup.event_control
    cgroup.procs
    debug.releasable
    notify_on_release
    release_agent
    tasks
    
查看 tasks 內容：

    # cat /cgroup/tasks
    
      1
      2
      3
      4
      ....
    以上數字表示 thread 執行緒的 ID，又稱為 TID。目錄代表群組，其下 tasks 群組中的 threads 集合。
   
備註：

* 虛擬檔案系統：

  未擁有物理裝置的檔案系統。
  
* 刪除群組：

  使用 release 
    
