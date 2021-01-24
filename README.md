# AIOps 手册

英文版见 <README_en.md>。

AIOps 的论文、演讲、开源库的汇总手册。按照[《企业AIOps实施建议白皮书》](https://www.rizhiyi.com/assets/docs/AIOps.pdf)中的场景分类进行收集和展示。

对于同一个场景，尽量提供比较新的链接。因为新论文里一般会引用和对比旧论文。

## 异常检测

### 指标

#### 单指标

* 清华裴丹团队举办的 KPI 异常检测比赛用数据(需注册登录) <http://iops.ai/competition_detail/?competition_id=5&flag=1>
    * 比赛前 5 名的分享：<http://workshop.aiops.org/>
    * 某博士生发的程序(未在参赛的 40 支队伍上看到名字哈)：<https://github.com/chengqianghuang/exp-anomaly-detector-AIOps>
* 清华/阿里巴巴开源的 Donut(基于 VAE 算法)：<https://github.com/haowen-xu/donut>
    * 清华开源的 Bagel(Donut改进型，基于 CVAE 算法)：<https://github.com/lizeyan/Bagel>
* 清华/百度的 opprentice 系统(14 个检测器，平均取参数值，随机森林)：<http://netman.cs.tsinghua.edu.cn/wp-content/uploads/2015/11/liu_imc15_Opprentice.pdf>
* 清华/南开/腾讯的 ADS 系统(ROCKA+opprentice+CPLE)，论文：<https://netman.aiops.org/wp-content/uploads/2018/12/bujiahao.pdf>
    * github上一个开源的CPLE实现：<https://github.com/tmadl/semisup-learn>
* 腾讯开源的 metis 系统(参考了 opprentice 实现)：<https://github.com/tencent/metis>
* 阿里巴巴开源的Time2Graph(基于序列片段的图迁移路径做异常检测)：<https://github.com/petecheng/Time2Graph>
* skyline
    * etsy 开源版(9 个检测器，简单投票)：<https://github.com/etsy/skyline>
    * etsy 未开源版的介绍(小波分解后分别过 KS 和广义 ESD 检验)：<https://vimeo.com/131581331>
    * lytics 公司用 golang 重写的：<https://github.com/lytics/anomalyzer>
    * 社区版(加入 Ionosphere 模块做反馈修正，使用 tsfresh 库)：<https://github.com/earthgecko/skyline>
    * 360 公司开源的异常检测，和skyline一样简单投票，不过自己另写了几个EWMA、iForest、同环比等检测器：<https://github.com/jixinpu/aiopstools/tree/master/aiopstools/anomaly_detection>
* 开源的时序特征值提取库 tsfresh：<http://tsfresh.readthedocs.io/en/latest/>
* arundo 开源的 adtk 时序异常检测 python 库：<https://github.com/arundo/adtk>
* netflix基于 PCA 算法的异常检测，跑在 Pig 上：<https://github.com/netflix/surus>
* twitter 的异常检测库，R 语言：<https://github.com/twitter/anomalydetection>
* numenta 公司，HTM 算法：<https://github.com/numenta/nupic>
    * 顺带还做了一个项目专门用来比较效果(和裴丹比赛的评价标准不太一样，裴的标准是异常点往后 7 个都算；NAB 标准是异常区间内前一半算满分，后一半衰减)：<https://github.com/numenta/NAB>
* 雅虎开源的时序预测和异常检测项目 EGADS：<https://github.com/yahoo/egads>
    * 对应解释论文的中文翻译版：<http://www.infoq.com/cn/articles/automated-time-series-anomaly-detection>
* 亿客行Expedia开源的异常检测项目 adaptive-alerting：<https://github.com/ExpediaDotCom/adaptive-alerting>
* RedHat公司CTO办公室开源的prometheus anomaly detector项目(基于傅里叶变换和Facebook的prophet预测算法)：<https://github.com/AICoE/prometheus-anomaly-detector>

#### 多指标

* CMU 做多指标模式提取和异常检测的 SPIRIT 系统，论文：<https://bitquill.net/pdf/spirit_vldb05.pdf>
* 清华裴丹团队做的多指标聚类 ROCKA 系统，论文：<https://netman.aiops.org/~peidan/ANM2018/8.DependencyDiscovery/LectureCoverage/2018IWQOS_ROCKA.pdf>
* 清华裴丹团队做的多指标异常检测 OmniAnomaly 开源实现，主要是对同一对象的多个指标，采用和单指标Donut类似的方法：<https://github.com/NetManAIOps/OmniAnomaly>
* 微软亚研做的多指标聚类 YADING 系统，论文：<https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/p457-ding.pdf>
* 北卡顾晓晖团队做云主机异常检测和根因定位的 UBL 系统(基于 SOM 算法)，论文：<http://dance.csc.ncsu.edu/papers/UBL.pdf> 
* 新加坡国立大学做传感器多变量指标异常检测的开源项目(基于 GAN 算法)：<https://github.com/LiDan456/MAD-GANs>

### 日志

* RedHat公司CTO办公室开源的Log Anomaly Detector项目(基于word2vec和SOM算法)：<https://github.com/AICoE/log-anomaly-detector>
* 香港中文大学团队收集的多篇日志异常检测相关论文和数据集(共87GB)：<https://github.com/logpai/loghub>
    * 他们也做了各种现有算法的开源实现和横向测试对比，报告见：<https://arxiv.org/pdf/1811.03509.pdf>
    * IBM云数据中心团队改进和开源的 Drain3 包，加强了持久化，自定义参数替换等：<https://github.com/IBM/Drain3>
* DeepLog 论文(包含模式检测、参数检测、工作流检测三部分)：<https://acmccs.github.io/papers/p1285-duA.pdf>
    * 开源实现：<https://github.com/wuyifan18/DeepLog>
    * 另一个开源实现，还实现了另外两种算法[LogAnomaly](https://www.ijcai.org/Proceedings/2019/658)和[RobustLog](https://dl.acm.org/doi/10.1145/3338906.3338931)，可切换：<https://github.com/donglee-afar/logdeep>
* 清华/南开/腾讯的 FT-tree 开源实现：<https://github.com/WeibinMeng/ft-tree>
* 清华/南开/百度的 LogClass 开源实现：<https://github.com/NetManAIOps/LogClass>
* 北卡顾晓晖团队做日志异常检测的 ELT 系统(拆分为粗粒度的 MAV 和细粒度的 MFG 两层)：<http://dance.csc.ncsu.edu/papers/srds11.pdf>
* NEC 美国实验室/北卡做云系统工作流监控的 CloudSeer 系统：<https://people.engr.ncsu.edu/gjin2/Classes/591/Spring2017/case-cloudseer.pdf>
* NEC 美国实验室 LogMine 系统：<http://www.cs.unm.edu/~mueen/Papers/LogMine.pdf>
* NEC 美国实验室/蚂蚁金服做的 LogLens 系统(在 LogMine 基础上，和 ELK 的 Grok 设计结合；并加上了对 traceid 的判断处理，支持序列异常检测)，论文：<http://120.52.51.14/www.cs.ucsb.edu/~bzong/doc/icdcs-18.pdf>
* 香港中文大学/华为的 POP 系统(和 LogMine 思路比较类似，在 Spark 上运行)：<http://www.cse.cuhk.edu.hk/lyu/_media/journal/pjhe_tdsc18.pdf>
* 国防科大的日志领域研究综述(日志监测部分比我前面列的老，但还提了基于源码的静态分析和基于虚拟机增强的日志内容改进两个方向，基本都是袁丁教授团队做的)：<http://www.jos.org.cn/1000-9825/4936.htm>
    * morningpaper 博客关于静态分析的 lprof 论文解析：<https://blog.acolyer.org/2015/10/08/lprof-a-non-intrusive-request-flow-profiler-for-distributed-systems/>
    * morningpaper 博客关于日志增强的 log20 论文解析：<https://blog.acolyer.org/2017/11/03/log20-fully-automated-optimal-placement-of-log-printing-statements-under-specified-overhead-threshold/>
* 其他商业公司：
    * Loomsystems(已被 serviceNow 收购，其对参数类型的 meter/gauge/timeless-gauge/histogram/invalid/root-cause 分类值得借鉴)：<https://www.loomsystems.com/hubfs/SophieTechnicalOverview.pdf>
    * coralogix(有基础的无关顺序的关联模式检测，对 XML/JSON 类型进行对象参数检测)：<https://coralogix.com/tutorials/what-is-coralogix-pattern-anomaly/>
    * zebrium(存 newsql，参数名称的自动识别值得借鉴)：<https://www.zebrium.com/blog/using-ml-to-auto-learn-changing-log-structures>

## 标注

### 指标异常标注

* 百度开源的指标异常标注工具：<https://github.com/baidu/Curve>
* 微软开源的指标异常工具：<https://github.com/Microsoft/TagAnomaly>
* 清华/建行做的指标批量标注 Label-less 项目(基于 iForest 异常检测和 DTW 相似度学习)：<
https://netman.aiops.org/wp-content/uploads/2019/10/Label-less-v2.pdf>

## 预测

### 单指标

* 脸书开源，时序预测：<https://github.com/facebook/prophet>
* 红帽开源，是 hawkular(已被 jaeger 取代)项目的一部分，在 ARIMA 基础上做了自动调参：<https://github.com/hawkular/hawkular-datamining>
* 360 开源，封装了LR、ARIMA、LSTM等通用算法做预测：<https://github.com/jixinpu/aiopstools/tree/master/aiopstools/timeseries_predict>
* 北卡顾晓晖团队做监控系统数据传输压缩的论文(先聚类并下发预测模型，agent上预测无偏差就不上报了)：<http://dance.csc.ncsu.edu/papers/ICAC09.pdf>

### 容量规划

* 谷歌 某 12.5k 规模集群的任务资源和机器数据：<https://github.com/google/cluster-data>
* 微软 Azure 云某区的云主机启停、 CPU 和内存时序数据：<https://github.com/Azure/AzurePublicDataset>
* 阿里云某 1.3k 规模集群的云主机、容器和后台任务的时序数据：<https://github.com/alibaba/clusterdata>
   * 使用该数据集做的天池调度算法大赛第6名"地球漫步"的开源版本：<https://github.com/NeuronEmpire/aliyun_schedule_semi>
* Trulia 开源，根据查询语句预测 Solr 集群的查询性能并调度：<https://github.com/trulia/thoth>

### 网络

* 南开张圣林，交换机 syslog 故障预测：<http://workshop.aiops.org/files/shenglinzhang2018prefix.pdf>

### 事件关联挖掘

* 微软亚研的 Log3C，日志和 KPI 的关联挖掘：<https://github.com/logpai/Log3C>
* 微软和吉林大学的论文：<http://www.microsoft.com/en-us/research/wp-content/uploads/2016/07/SIGKDD-2014-Correlating-Events-with-Time-Series-for-Incident-Diagnosis.pdf>
    * 360 公司按照该论文的开源实现：<https://github.com/jixinpu/aiopstools/tree/master/aiopstools/association_analysis>

## 根因分析

### 调用链

这块没啥好说的，属于很有用，但比拼的不是 AI：

* zipkin/brave
* skywalking
* pinpoint
* opencensus
* 萨尔布吕肯大学Jonathan Mace，利用层次聚类尽量避免采样时丢失罕见个例：<https://people.mpi-sws.org/~jcmace/papers/lascasas2018weighted.pdf>

### 多维KPI分析

* 清华/百度的HotSpot论文，有多维属性的 KPI 故障范围分析：<http://netman.ai/wp-content/uploads/2018/03/sunyq_IEEEAccess_HotSpot.pdf>
* 清华/建行的FluxRank论文，在服务级故障时，快速定位到小范围的主机层问题并重启：<https://netman.aiops.org/wp-content/uploads/2019/08/liuping-camera-ready.pdf>

### 时序相关性分析

* etsy 开源版，基于 elasticsearch 实现的 fastDTW 时序相关性排序：<https://github.com/etsy/oculus>
* linkedin 开源的基于 SAX 的异常检测和相关性计算库：<https://github.com/linkedin/luminol>
    * 此外，还有一个完整系统的介绍分享：<https://docs.google.com/presentation/d/1DWMNgoAtxuK8ZbFJOpq5vt3dEz5_4ptMuLtoTUjQ_ro/pub?start=false&loop=false&delayms=3000&slide=id.p>
* Uber 公司的 Argos 系统，只有介绍文章：<https://eng.uber.com/argos/>

### 解决方案相关性推荐

* 佛罗里达国际大学/IBM的论文，基于 CNN 做工单的关联和推荐，重点在如何过滤和提取工单文本的有效特征值：<https://www.researchgate.net/publication/318373831_STAR_A_System_for_Ticket_Analysis_and_Resolution>

## 告警归并

* 360 开源，基于 Apriori 算法：<https://github.com/jixinpu/aiopstools/blob/master/examples/alarm_convergence.py>
* anodot 公司论文，第三部分，利用 SAE 和 LDA 做 KPI 和告警的拓扑：<http://proceedings.mlr.press/v71/toledano18a/toledano18a.pdf>
* 其他商业公司：
    * [moogsoft](https://docs.moogsoft.com/) 公司(专门做告警处理的AIOps创业公司)有关技术实现的演讲：<https://docs.google.com/presentation/d/1F-8eop-9ffCpX4trOJS28FXATAFlQkgkfnDV_Zqnkuo/edit?pref=2&pli=1#slide=id.g990524d96_0_0>

## 图谱

* 清华大学徐葳团队，状态图谱解决 OpenStack 问题：<http://iiis.tsinghua.edu.cn/~weixu/files/apsys-yong-slides.pdf>
* 徐葳早年论文，用状态图来辅助开源项目更好的修改 logging 代码：<http://iiis.tsinghua.edu.cn/~weixu/files/slaml10-rabkin.pdf>
* 宜信张真的演讲：[WOT2018 -张真-运维机器人之任务决策系统演讲](https://pan.baidu.com/s/1gSjJZIXswOPoeQzZ6cJT1g?errno=0&errmsg=Auth%20Login%20Sucess&&bduss=&ssnerror=0&traceid=)
* CA/加泰罗尼亚理工大学，用日志和指标构建的基于图谱的微服务根因分析系统：<https://www.researchgate.net/publication/336585890_Graph-based_Root_Cause_Analysis_for_Service-Oriented_and_Microservice_Architectures>
* 微众银行的智能运维系列分享第八篇(给了非常详细的节点属性和边属性设计，比 CA 的更细节)：[事件指纹库：构建异常案例的“博物馆”](https://mp.weixin.qq.com/s/M8tcS8q6sPPRRebAJkrb7Q)

## 行为异常

* 北卡顾晓晖团队做程序行为异常分析的 PerfScope 系统(利用 LTTng 在线采集系统调用，配合 Apriori 算法)，论文：<http://dance.csc.ncsu.edu/papers/socc14.pdf>
* ee-outliers 开源项目，利用 word2vec 做 osquery 输出的事件异常检测：<https://github.com/NVISO-BE/ee-outliers>
* ubad 开源项目，利用 LSTM 和 OCSVM 做 osquery 输出的用户行为事件异常检测：<https://github.com/morrigan/user-behavior-anomaly-detector>
* 阿里云天池算法大赛扫描爆破部分，第10名的开源介绍：<https://github.com/wufanyou/aliyun_safety>
* Security Repo数据集，Mike Sconzo收集的各种和安全运维有关的数据：<https://www.secrepo.com/>
* 其他商业公司：
    * ExtraHop：<https://docs.extrahop.com/current/>

## 扩展阅读

* 感谢 @linjinjin123 的 [awesome-AIOps](https://github.com/linjinjin123/awesome-AIOps) 库，但我认为运维人员可能更需要的是一个从实用场景出发的归类。
* @zhuyiche 的 [awesome-anomaly-detection](https://github.com/zhuyiche/awesome-anomaly-detection) 库，专精在异常检测领域的论文收集。
* @logpai 的 [log-survey](https://github.com/logpai/log-survey) 库，专精在日志领域的论文和研究者收集，不光包括分析，还包括生成增强、压缩等。
