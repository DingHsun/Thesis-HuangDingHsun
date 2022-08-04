# Thesis-HuangDingHsun
國立中山大學應用數學系  
黃鼎勳碩士論文  
以深度學習張量特徵萃取實現超解析成像  
Tensor feature extraction in deep learning for
super-resolution imaging  

本研究的目的在於如何使用特徵萃取與深度學習的方法，來生成取得高解析度高畫質的影像。在深度學習（Deep learning）中，資料的特徵工程、重要變數分析和模型選擇等等，是訓練模型前重要的前處理過程，而特徵萃取能夠提取資料的重要特徵，並減少資料的記憶體儲存，使其能有效加快網路的學習。相較於輸入原始資料（原始影像），這對於訓練深度學習網路而言將是一個很好的初始步驟。
	
在特徵萃取的部分使用 SVD 分解（Singular Value Decomposition）提取重要特徵，擷取 99% 之重要資訊並對資料進行 1.5 至 2 倍不等的壓縮比例，同時進行資料壓縮和特徵萃取工程。而在 SVD 分解的過程中發現，去除那 1% 的特徵向量所對應的資料，有助於將影像去除噪音、低頻雜訊，使得影像在超解析成像（Super-resolution imaging）的過程中不會受到雜訊噪音的干擾，不管是在主觀的視覺上或是客觀的數值上都有更好的結果。
	
然而現今許多資料不再是向量（vector）而是以張量（tensor）的形式，例如一張灰階的影像將其數值化可以看做是一個矩陣，彩色影像以 RGB 數值化則可以看做是一個三維空間的張量。但以往所熟知的 SVD 分解方式，僅僅只能處理矩陣的資料，而不能處理更高維度的資料，因此將張量矩陣化（Matricization）的方式便由此而生，HOSVD（High-Order Singular Value Decomposition）成為能夠對高階張量做特徵工程的方式之一。HOSVD  的運算過程是將一個高階張量的資料對其矩陣化後，形成一個矩陣的資料再做 SVD 分解之特徵萃取，萃取完特徵後再以原本矩陣化的過程還原回高階張量的形式。
	
在生成高解析度高畫質的影像上，使用深度學習的卷積神經網路（Convolution Neural Network, CNN）模型架構，並以人臉為資料訓練模型。本篇論文會使用三種 CNN 架構之模型，SRCNN（Super-Resolution CNN）、VDSR（Very Deep Super-Resolution）和 ResNet（Deep residual network），探討各個模型的架構之優劣和特性，並分別對資料有無使用 HOSVD 前處理進行實驗。
	
實驗以 64x64 彩色影像為輸入， 128x128 提升一倍之高解析度高畫質影像為輸出，並以峰值訊噪比（Peak signal-to-noise ratio, PSNR）為主要指標， PSNR 越高代表輸出影像與原始高畫質影像越接近。結果顯示每個模型有使用 HOSVD 特徵萃取相比於沒有使用之 PSNR 皆有所提升，且在主觀視覺上有明顯變好的趨勢。
