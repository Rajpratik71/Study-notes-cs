#adb

>* path : Android_sdk

>* adb logcat -c
>* adb logcat -s tag,tag2,tag3

#ndk
>* nkd-build 
>* nkd-build clean

#inet c
```
   char addr_tmp[INET_ADDRSTRLEN];
                inet_ntop(AF_INET, &(peeraddr.sin_addr), addr_tmp, INET_ADDRSTRLEN);
                LOGI("==> accept client %s:%d by socket %d\n",
                          addr_tmp, ntohs(peeraddr.sin_port), conn);
```
