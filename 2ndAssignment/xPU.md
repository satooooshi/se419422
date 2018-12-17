#xPU
##APU
Accelerated Processing Unit。目前还没有AI公司将自己的处理器命名为APU，因为AMD早就用过APU这个名字了。APU是AMD的一个处理器品牌。AMD在一颗芯片上集成传统CPU和图形处理器GPU，这样主板上将不再需要北桥，任务可以灵活地在CPU和GPU间分配。AMD将这种异构结构称为加速处理单元，即APU。
Audio Processing Unit。声音处理器，顾名思义，处理声音数据的专用处理器。不多说，生产APU的芯片商有好多家。声卡里都有。
##BPU
Brain Processing Unit。地平线机器人（Horizon Robotics）以BPU来命名自家的AI芯片。地平线是一家成立于2015年的start-up，总部在北京，目标是“嵌入式人工智能全球领导者”。地平线的芯片未来会直接应用于自己的主要产品中，包括：智能驾驶、智能生活和智能城市。地平线机器人的公司名容易让人误解，以为是做“机器人”的，其实不然。地平线做的不是“机器”的部分，是在做“人”的部分，是在做人工智能的“大脑”，所以，其处理器命名为BPU。相比于国内外其他AI芯片start-up公司，地平线的第一代BPU走的相对保守的TSMC的40nm工艺。BPU已经被地平线申请了注册商标，其他公司就别打BPU的主意了。
Biological Processing Unit。一个口号“21 世纪是生物学的世纪”忽悠了无数的有志青年跳入了生物领域的大坑。其实，这句话需要这么理解，生物学的进展会推动21世纪其他学科的发展。比如，对人脑神经系统的研究成果就会推动AI领域的发展，SNN结构就是对人脑神经元的模拟。不管怎么说，随着时间的推移，坑总会被填平的。不知道生物处理器在什么时间会有质的发展。
Bio-Recognition Processing Unit。生物特征识别现在已经不是纸上谈兵的事情了。指纹识别已经是近来智能手机的标配，电影里的黑科技虹膜识别也上了手机，声纹识别可以支付了...不过，除了指纹识别有专门的ASIC芯片外，其他生物识别还基本都是sensor加通用cpu/dsp的方案。不管怎样，这些芯片都没占用BPU或BRPU这个宝贵位置。
##CPU
CPU就不多说了，也不会有AI公司将自己的处理器命名为CPU的。不过，CPU与AI处理器并不冲突。
首先，很多公司的AI处理器中还是会使用CPU做控制调度。比如，wave computing用的是Andes的CPU core；Mobileye用了好几个MIPS的CPU core；国内的某些AI芯片公司用的ARM的CPU core。
此外，在现有的移动市场的AP中，在CPU之外，再集成一两个AI加速器IP（例如针对视觉应用的DSP，见VPU部分）也是一种趋势。例如，华为近期就在为其集成了AI加速器的麒麟970做宣传。
##DPU
Deep-Learning Processing Unit。深度学习处理器。DPU并不是哪家公司的专属术语。在学术圈，Deep Learning Processing Unit（或processor）被经常提及。例如ISSCC 2017新增的一个session的主题就是Deep Learning Processor。
Deep Learning Unit。深度学习单元。Fujitsu（富士通）最近高调宣布了自家的AI芯片，命名为DLU。名字虽然没什么创意，但是可以看到DLU已经被富士通标了“TM”，虽然TM也没啥用。在其公布的信息里可以看到，DLU的ISA是重新设计的，DLU的架构中包含众多小的DPU（Deep Learning Processing Unit）和几个大的master core（控制多个DPU和memory访问）。每个DPU中又包含了16个DPE（Deep-Learning Processing Element），共128个执行单元来执行SIMD指令。富士通预计2018财年内推出DLU。
Deep Learning Accelerator。深度学习加速器。NVIDA宣布将这个DLA开源，给业界带来了不小的波澜。大家都在猜测开源DLA会给其他AI公司带来什么。参考这篇吧"从Nvidia开源深度学习加速器说起"
Dataflow Processing Unit。数据流处理器。创立于2010年的wave computing公司将其开发的深度学习加速处理器称为Dataflow Processing Unit(DPU)，应用于数据中心。Wave的DPU内集成1024个cluster。每个Cluster对应一个独立的全定制版图，每个Cluster内包含8个算术单元和16个PE。其中，PE用异步逻辑设计实现，没有时钟信号，由数据流驱动，这就是其称为Dataflow Processor的缘由。使用TSMC 16nm FinFET工艺，DPU die面积大概400mm^2，内部单口sram至少24MB，功耗约为200W，等效频率可达10GHz，性能可达181TOPS。前面写过一篇他家DPU的分析，见传输门AI芯片|浅析Yann LeCun提到的两款Dataflow Chip。
Data-storage Processing Unit。数据存储处理器。深圳大普微电子开发固态硬盘SSD主控芯片。SSD的主控也是一个很大的市场，国内在这个方向上奋斗的公司不少。
Digital Signal Processor。数字信号处理器。芯片行业的人对DSP都不陌生，设计DSP的公司也很多，TI，Qualcomm，CEVA，Tensilica，ADI，Freescale等等，都是大公司，此处不多做介绍。相比于CPU，DSP通过增加指令并行度来提高数字计算的性能，如SIMD、VLIW、SuperScalar等技术。面对AI领域新的计算方式（例如CNN、DNN等）的挑战，DSP公司也在马不停蹄地改造自己的DSP，推出支持神经网络计算的芯片系列。在后面VPU的部分，会介绍一下针对Vision应用的DSP。和CPU一样，DSP的技术很长时间以来都掌握在外国公司手里，国内也不乏兢兢业业在这方向努力的科研院所，如清华大学微电子所的Lily DSP（VLIW架构，有独立的编译器），以及国防科大的YHFT-QDSP和矩阵2000。但是，也有臭名昭著的“汉芯”。
##EPU
Emotion Processing Unit。Emoshape 并不是这两年才推出EPU的，号称是全球首款情绪合成（emotion synthesis）引擎，可以让机器人具有情绪。但是，从官方渠道消息看，EPU本身并不复杂，也不需要做任务量巨大的神经网络计算，是基于MCU的芯片。结合应用API以及云端的增强学习算法，EPU可以让机器能够在情绪上了解它们所读或所看的内容。结合自然语言生成(NLG)及WaveNet技术，可以让机器个性化的表达各种情绪。例如，一部能够朗读的Kindle，其语音将根据所读的内容充满不同的情绪状态。
##FPU
先说一个最常用的FPU缩写：Floating Point Unit。浮点单元，不多做解释了。现在高性能的CPU、DSP、GPU内都集成了FPU做浮点运算。
Force Processing Unit。原力处理器.
##GPU
Graphics Processing Unit。图形处理器。GPU原来最大的需求来自PC市场上各类游戏对图形处理的需求。但是随着移动设备的升级，在移动端也逐渐发展起来。
Graph Streaming Processor。图形流处理器。这是ThinCI（取意think-eye）提出的缩写。ThinCI是一家致力于打造deep learning和computer vision芯片的start-up，由4名Intel前员工创立于2010年，总部在Sacramento，在印度也有研发人员。ThinCI的视觉芯片瞄准了自动驾驶应用，投资方有世界顶级汽车零部件供应商公司日本电装DENSO。在刚结束的hotchip会议上，ThinCI介绍了他们的GSP（于是本文作者将ThinCI从VPU部分移到了这里），使用了多种结构性技术来实现任务级、线程级、数据级和指令级的并行。GSP使用TSMC 28nm HPC+工艺，功耗预计2.5W。
##HPU
Holographic Processing Unit。全息处理器。Microsoft专为自家Hololens应用开发的。第一代HPU采用28nm HPC工艺，使用了24个Tensilica DSP并进行了定制化扩展。HPU支持5路cameras、1路深度传感器（Depth sensor）和1路动作传感器（Motion Sensor）。Microsoft 在最近的CVPR 2017上宣布了HPU2的一些信息。HPU2将搭载一颗支持DNN的协处理器，专门用于在本地运行各种深度学习。指的一提的是，HPU是一款为特定应用所打造的芯片，这个做产品的思路可以学习。据说Microsoft评测过Movidius（见VPU部分）的芯片，但是觉得无法满足算法对性能、功耗和延迟的要求，所有才有了HPU。
##IPU
Intelligence Processing Unit。智能处理器。
Image Cognition Processor。图像认知处理器ICP，加拿大公司CogniVue开发的用于视觉处理和图像认知的IP。跑个题，CogniVue一开始是Freescale的IP供应商，后来于2015年被Freescale收购以进一步加强ADAS芯片的整合开发；随后，Freescale又被NXP 118亿美元拿下；还没完，高通近400亿美元吞并了NXP。 现在NXP家的ADAS SOC芯片S32V系列中，就用到了两个ICP IP。
Image Processing Unit。图像处理器。一些SOC芯片中将处理静态图像的模块称为IPU。但是，IPU不是一个常用的缩写，更常见的处理图像信号的处理器的缩写为下面的ISP。
Image Signal Processor 。图像信号处理器。这个话题也不是一个小话题。ISP的功能，简单的来说就是处理camera等摄像设备的输出信号，实现降噪、Demosaicing、HDR、色彩管理等功能。以前是各种数码相机、单反相机中的标配。Canon、Nikon、Sony等等，你能想到的出数码相机的公司几乎都有自己的ISP。进入手机摄影时代，人们对摄影摄像的要求也越来越高，ISP必不可少。说回AI领域，camera采集图像数据，也要先经过ISP进行处理之后，再由视觉算法（运行在CPU、GPU或ASIC加速器上的）进行分析、识别、分类、追踪等进一步处理。也许，随着AI技术发展，ISP的一些操作会直接被end-2-end的视觉算法统一。
##KPU
Knowledge Processing Unit。 嘉楠耘智（canaan）号称2017年将发布自己的AI芯片KPU。嘉楠耘智要在KPU单一芯片中集成人工神经网络和高性能处理器，主要提供异构、实时、离线的人工智能应用服务。这又是一家向AI领域扩张的不差钱的矿机公司。作为一家做矿机芯片（自称是区块链专用芯片）和矿机的公司，嘉楠耘智累计获得近3亿元融资，估值近33亿人民币。据说嘉楠耘智近期将启动股改并推进IPO。
##MPU
Micro Processing Unit。微处理器。
Mind Processing Unit。意念处理器，听起来不错。“解读脑电波”，“意念交流”，永恒的科幻话题。如果采集大量人类“思考”的脑电波数据，通过深度学习，再加上强大的意念处理器MPU，不知道能否成为mind-reader。如果道德伦理上无法接受，先了解一下家里宠物猫宠物狗的“想法”也是可以的吗。再进一步，从mind-reader发展为mind-writer，持续升级之后，是不是就可以成为冰与火中的Skinchanger？
##NPU
Neural-Network Processing Unit。与GPU类似，神经网络处理器NPU已经成为了一个通用名词，而非某家公司的专用缩写。由于神经网络计算的类型和计算量与传统计算的区别，导致在进行NN计算的时候，传统CPU、DSP甚至GPU都有算力、性能、能效等方面的不足，所以激发了专为NN计算而设计NPU的需求。
Neural/Neuromorphic Processing Unit。神经/神经形态处理器。这和上面的神经网络处理器还有所不同。而且，一般也不以“处理器”的名字出现，更多的时候被称为“神经形态芯片（Neuromorphic Chip）”或者是“类脑芯片（Brain-Inspired Chip）”。这类AI芯片不是用CNN、DNN等网络形式来做计算，而是以更类似于脑神经组成结构的SNN（Spiking Neural Network）的形式来进行计算。
##OPU
Optical-Flow Processing Unit。光流处理器。用ASIC IP来做加速应该是要的。
##PPU
Physical Processing Unit。物理处理器。要先解释一下物理运算，就知道物理处理器是做什么的了。物理计算，就是模拟一个物体在真实世界中应该符合的物理定律。具体的说，可以使虚拟世界中的物体运动符合真实世界的物理定律，可以使游戏中的物体行为更加真实，例如布料模拟、毛发模拟、碰撞侦测、流体力学模拟等。开发物理计算引擎的公司有那么几家，使用CPU来完成物理计算，支持多种平台。但是，Ageia应该是唯一一个使用专用芯片来加速物理计算的公司。Ageia于2006年发布了PPU芯片PhysX，还发布了基于PPU的物理加速卡，同时提供SDK给游戏开发者。2008年被NVIDIA收购后，PhysX加速卡产品被逐渐取消，现在物理计算的加速功能由NVIDIA的GPU实现，PhysX SDK被NVIDIA重新打造。
##QPU
Quantum Processing Unit。量子处理器。量子计算机也是近几年比较火的研究方向。作者承认在这方面所知甚少。可以关注这家成立于1999年的公司D-Wave System。DWave大概每两年可以将其QPU上的量子位个数翻倍一次。
##RPU
Resistive Processing Unit。阻抗处理单元RPU。这是IBM Watson Research Center的研究人员提出的概念，真的是个处理单元，而不是处理器。RPU可以同时实现存储和计算。利用RPU阵列，IBM研究人员可以实现80TOPS/s/W的性能。
Ray-tracing Processing Unit。光线追踪处理器。Ray tracing是计算机图形学中的一种渲染算法，RPU是为加速其中的数据计算而开发的加速器。现在这些计算都是GPU的事情了。
##SPU
Streaming Processing Unit。流处理器。流处理器的概念比较早了，是用于处理视频数据流的单元，一开始出现在显卡芯片的结构里。可以说，GPU就是一种流处理器。甚至，还曾经存在过一家名字为“Streaming Processor Inc”的公司，2004年创立，2009年，随着创始人兼董事长被挖去NVIDIA当首席科学家，SPI关闭。
Speech-Recognition Processing Unit。语音识别处理器，SPU或SRPU。这个缩写还没有公司拿来使用。现在的语音识别和语义理解主要是在云端实现的，比如科大讯飞。科大讯飞最近推出了一个翻译机，可以将语音传回云端，做实时翻译，内部硬件没有去专门了解。和语音识别相关的芯片如下。
Space Processing Unit。空间处理器，高大上，有没有。全景摄像，全息成像，这些还都是处理我们的生活空间。当面对广阔的太阳系、银河系这些宇宙空间，是不是需要新的更强大的专用处理器呢？飞向M31仙女座星系，对抗黑暗武士，只靠x86估计是不行的。
##TPU
Tensor Processing Unit。Google的张量处理器。2016年AlphaGo打败李世石，2017年AlphaGo打败柯洁，两次人工智能催化事件给芯片行业带来的冲击无疑就是TPU的出现和解密。Google在2017年5月的开发者I/O大会上正式公布了TPU2，又称Cloud TPU。相比于TPU1，TPU2既可以用于training，又可以用于inference。TPU1使用了脉动阵列的流处理结构，具体的细节可以参考文章“Google TPU 揭密”。
##VPU
Vision Processing Unit。视觉处理器VPU也有希望成为通用名词。作为现今最火热的AI应用领域，计算机视觉的发展的确能给用户带来前所未有的体验。为了处理计算机视觉应用中遇到的超大计算量，多家公司正在为此设计专门的VPU。
Video Processing Unit。视频处理器。处理动态视频而不是图像，例如进行实时编解码。
Vector Processing Unit。向量处理器。标量处理器、向量处理器、张量处理器，这是以处理器处理的数据类型进行的划分。现在的CPU已经不再是单纯的标量处理器，很多CPU都集成了向量指令，最典型的就是SIMD。向量处理器在超级计算机和高性能计算中，扮演着重要角色。基于向量处理器研发AI领域的专用芯片，也是很多公司的选项。例如，前面刚提到Movidius的Myriad2中，就包含了12个向量处理器。
##WPU
Wearable Processing Unit。一家印度公司Ineda Systems在2014年大肆宣传了一下他们针对IOT市场推出的WPU概念，获得了高通和三星的注资。Ineda Systems研发的这款“Dhanush WPU”分为四个级别，可适应普通级别到高端级别的可穿戴设备的运算需求，可以让可穿戴设备的电池达到30天的持续续航、减少10x倍的能耗。但是，一切似乎在2015年戛然而止，没有了任何消息。只在主页的最下端有文字显示，Ineda将WPU申请了注册商标。
