App性能的测试原理

一、CPU测试

String cpuStatPath = "/proc/" + processPid + "/stat";
RandomAccessFile processCpuInfo = new RandomAccessFile(cpuStatPath, "r");

二、内存测试

os.writeBytes("dumpsys meminfo " + pid + "\n");

三、流量测试

rcvTraffic = TrafficStats.getUidRxBytes(Integer.parseInt(uid));//下载的流量
sndTraffic = TrafficStats.getUidTxBytes(Integer.parseInt(uid));//上传的流量

四、电量测试

int level = intent.getIntExtra(BatteryManager.EXTRA_LEVEL, 0);//获取电池当前的电量	
int scale = intent.getIntExtra(BatteryManager.EXTRA_SCALE, -1);//表示电量的最大值
totalBatt = String.valueOf(level * 100 / scale);//当前电量的计算

五、FPS测试

注意：需要root，如果手机没有root，则测试数据是不对的！

os.writeBytes("service call SurfaceFlinger 1013" + "\n");



