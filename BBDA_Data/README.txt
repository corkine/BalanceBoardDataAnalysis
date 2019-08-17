各脚本使用方法：
Excel2CSV.py
	遍历此文件夹以及所有子文件夹的 .xlsx 文件，并且在相同目录下生成 .csv 文件。

MoveAndRenameFiles.py
	双击运行，命令行界面。如果不可运行，则打开 CMD，切换到当前目录，执行 python MoveAndRenameFiles.py 运行。输入 y，按下回车，表示执行清理工作，将所有 .xlsx 文件移动到 xlsx 目录下，将所有 .log 文件移动到 log 目录下，将所有 output.csv 结尾的文件移动到 output 目录下，将所有 .csv 结尾的文件移动到 csv 目录下。输入 r，按下回车，则执行相反步骤，将各文件夹文件取出来放到根目录下。

BBDAManager.jar
	所有被试元数据存在于 data.dta 二进制文件中，包括实验开始时间、结束时间、被试姓名、id和实验条件。
使用 BBDAManager.jar 来管理此 data.dta 数据。双击即可运行。或者在命令行界面执行 java -jar BBDAManager.jar

BBDAManager.jar 基本批处理
	点击 Batch 按钮，再点击确定，复制所有的文本，然后在 CMD 下输入，将会自动执行，这些代码会调用 BBDA。jar 程序处理数据，结果为 xxx_output.csv。

BBDAManager.jar 高级批处理
	打开 CMD,切换到本目录下，执行 java -cp BBDA.jar com.mazhangjing.lab.Batch 即可进入批处理界面，批处理界面需要被试信息。按照以下步骤获取被试信息：
	打开 BBDAManager 程序，点击 Batch 按钮，清空所有内容，点击确定，复制所有文本，在批处理界面直接粘贴即可。粘贴完毕后按下 Ctrl + Z，然后按下回车，自动开始进行批处理。

警告：批处理程序会利用 Java8 Stream 并行流 API（FatchAndJoin），会几乎完全利用 CPU 所有核心的所有性能，CPU 占用率将会一直保持 100%，直到程序处理完毕。在一台 8 核心 16 线程的 Core i7 (Gen4) 上处理，请注意电源和插座电源供给稳定，请勿使用劣质电源，使用劣质电源 + 16 线程 CPU 最高性能状态，有一定几率会导致电源过载，或者插排跳闸。每个被试大约要进行 1 亿次数据查找和匹配，高级批处理性能相较于串行Java程序，效率提高了n倍（n为计算机线程的数量），相较于使用矩阵的 Matlab 或者 使用 numpy 的 Python，性能理论提升 50n 倍（n为计算机线程的数量）。极限情况下，基于 Stream 的 Java8，相较于脚本语言，处理此数据的性能提升 1000 倍以上。

