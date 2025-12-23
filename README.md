# Realtek-8851BU-Wireless-LAN-Wifi-6-USB-NIC-For-Ubuntu-Driver


## Ubuntu24.04 版本无线网卡驱动
提示错误
```
|     ^~~~~~~~~~~~~~~~~~~~~~~~~~
os_dep/linux/ioctl_cfg80211.c:11003:25: error: initialization of ‘int (*)(struct wiphy *, struct wireless_dev *, unsigned int,  int *)’ from incompatible pointer type ‘int (*)(struct wiphy *, struct wireless_dev *, unsigned int,  int *)’ [-Werror=incompatible-pointer-types]
11003 |         .get_tx_power = cfg80211_rtw_get_txpower,
      |                         ^~~~~~~~~~~~~~~~~~~~~~~~
```   
修改了 os_dep/linux/ioctl_cfg80211.c de 两个函数
```
static int cfg80211_rtw_get_txpower(struct wiphy *wiphy,
                                    struct wireless_dev *wdev,
                                    unsigned int link_id,
                                    int *dbm)
{
    RTW_INFO("%s\n", __func__);
    *dbm = 12;
    return 0;
}
static int cfg80211_rtw_get_txpower(struct wiphy *wiphy,
                                    struct wireless_dev *wdev,
                                    unsigned int link_id,
                                    int *dbm);
```
