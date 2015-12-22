MATLAB Active Learning Toolbox for Remote Sensing.
<br>(now also at GitHub: <a href='https://github.com/IPL-UV/altoolbox'>https://github.com/IPL-UV/altoolbox</a>)<br>
<br>
<h1>Instructions</h1>

<h3>Quick setup</h3>

<ol><li>Download the last release and install it on your computer. Latest version is at:<br>
<ul><li><a href='https://altoolbox.googlecode.com/archive/ALToolbox_v0.5.2.zip'>https://altoolbox.googlecode.com/archive/ALToolbox_v0.5.2.zip</a>, or at<br>
</li><li><a href='https://github.com/IPL-UV/altoolbox/archive/ALToolbox_v0.5.2.zip'>https://github.com/IPL-UV/altoolbox/archive/ALToolbox_v0.5.2.zip</a>
</li></ul></li><li>Download <a href='https://altoolbox.googlecode.com/files/multisvm_binaries_v2.zip'>multisvm_binaries_v2.zip</a>, uncompress it, copy the binary corresponding to your platform in the ALTB directory and rename it to 'multisvm' (or 'multisvm.exe' if you are using Windows).<br>
</li><li>If you use Windows 64 bits you will also need to download <a href='https://altoolbox.googlecode.com/files/mingw64-runtime.zip'>mingw64-runtime.zip</a>. Save the contents in the ALTB directory or anywhere in your system path.<br>
</li><li>Run 'demo.m'.</li></ol>

<h3>What's next?</h3>

The ALTB code is well commented. Read the code in demo.m and in AL.m, which is the core of the toolbox. If you only want to use its methods, call AL.m with the appropriate parameters. If you want to include a new method and share it, look inside AL.m. There is basically a main loop with three steps:<br>
<br>
<ol><li>An SVM is trained with a given training/validation set.<br>
</li><li>The obtained model is used on a set of candidates.<br>
</li><li>The prediction is ranked according one of the AL methods, a set of samples from the candidate set is chosen, and the process is repeated.</li></ol>

Be careful, as we divide 'uncertainty' criteria (like margin sampling, i.e. how uncertain the sample is for the current model) from 'diversity' criteria (like ABD, i.e. how much selected samples are different between each other). Please follow this logic in your implementation.<br>
<br>
If you develop a new method and want to include it in the library for everyone to use and test, contact us using this project web page.<br>
<br>
<h2>Compiling multisvm</h2>

If you want to compile multisvm you will need the Torch3 library. You can download it from <a href='http://www.torch.ch/torch3/downloads.php'>http://www.torch.ch/torch3/downloads.php</a>.<br>
<br>
Read the instructions to compile the library and install it somewhere in your system. For multisvm, you need to include the 'core' and 'kernels' modules at least, but if you want to include all Torch3 modules it won't hurt.<br>
<br>
Once you have Torch3 compiled, take a look at the Makefile provided with the toolbox and modify it for your system. Usually, you only need to change the path where Torch3 is installed. Then run 'make' in a terminal and it should compile.<br>
<br>
<h1>References</h1>

<ol><li>Tuia, D.; Volpi, M.; Copa, L.; Kanevski, M.; Munoz-Mari, J.; , "A Survey of Active Learning Algorithms for Supervised Remote Sensing Image Classification," Selected Topics in Signal Processing, IEEE Journal of , vol.5, no.3, pp.606-617, June 2011. DOI: 10.1109/JSTSP.2011.2139193. URL: <a href='http://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=5742970&isnumber=5767682'>http://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&amp;arnumber=5742970&amp;isnumber=5767682</a>
</li><li>Tuia, D.; Muñoz-Marí, J.; , "Learning user's confidence for active learning," Geoscience and Remote Sensing, IEEE Transactions on, in press. DOI: 10.1109/TGRS.2012.2203605. URL:<a href='http://ieeexplore.ieee.or/xpls/abs_all.jsp?arnumber=6247502'>http://ieeexplore.ieee.or/xpls/abs_all.jsp?arnumber=6247502</a>
</li><li>Muñoz-Marí, J.; Tuia, D.; Camps-Valls, G.; , "Semisupervised Classification of Remote Sensing Images With Active Queries," Geoscience and Remote Sensing, IEEE Transactions on , vol.PP, no.99, pp.1-12, 0. DOI: 10.1109/TGRS.2012.2185504. URL: <a href='http://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6166388&isnumber=4358825'>http://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&amp;arnumber=6166388&amp;isnumber=4358825</a>