=================================================================

The test code for the Class RooBernsteinEffi is C11 compliant. 
[i.e. to compile on fly in lxplus you can set:  
scl enable devtoolset-7 tcsh]

Executables are:

testGene <= Usage: ./testGene [Q2Bin]  [where QBin2=0,1,2,3,4,5,6,7,8]

            This program: 
	    
		- reads the MC file for the generated events without filter: gen_B0_miniaodWithoutGenCuts.root;
	    
 		- fits the generated events angular distributions [for a Q2Bin] with the P-Wave model for a Q2Bin;
	    
		- extracts the model parameters and write them in a text file: ListGenValues-2016-Q2Bin-[Q2Bin].txt;
	    
		- using the same model, it generates a Mini MC angular distribution (with statistic = [NFact]x[original number of MC generated events];
	    
		- test the Mini MC generated events distribution fitting it with the P-Wave model;
	    
		- produces the output root file testGene-2016-Q2Bin-[Q2Bin].root;
	    
		- produces B0-Generated-PdfFit-2016-Q2Bin-[Q2Bin].pdf/.png with the projections of the fit to the MC     gen events distribution;
	    
		- produces B0-Generated-MiniMC-PdfFit-2016-globalpdf/.png  with the projections of the fit to the MiniMC gen events distribution.
	    
	    
	    
	     
	    
testGeneReFit <= Usage: ./testGeneReFit    [Q2Bin]    [where QBin2=0,1,2,3,4,5,6,7,8]

            This program: 
	    
		- contains a full example of the use of the efficiency class RooEffiBernstein in roofit 

		- reads the MC file 2016MC_RECO_p1p2p3_newtag_LMNR_addW_add4BDT_addvars_bestBDTv4.root;
	    
		- reads the model list parameters ListGenValues-2016-Q2Bin-[Q2Bin].txt, previously generated by testGene;
	    
		- reads the efficiency coefficents for the Bernstein Polynomial from  ListParValues-2016-Q2Bin-[Q2Bin]-Bins-25-25-25-BernDeg-[max1]-[max2]-[max3]-integraBin.plo where max1,max2,max3 are the maximum polynomial degrees for cosL,cosK and phi;
	    
		- fits the reconstructed events angular distribution with a UML of the P-wave PDFxEfficiency;
	    
		- produces the output file testGeneReFit-2016-Q2Bin-[Q2Bin]-Bins-25-25-25-BernDeg-[max1]-[max2]-[max3]-integraBin.root, with a the canvas "ClosurePlots" where are stored the projections of the reco distribution and, superimposed in red, teh fit.  
		 
		 
testEffi3DB0-2016-makeHisto <= Usage:  ./testEffi3DB0-2016-makeHisto     QBin2     [where QBin2=0,1,2,3,4,5,6,7,8] 

            This program: 
	    
		- reads the MC file 2016MC_RECO_p1p2p3_newtag_LMNR_addW_add4BDT_addvars_bestBDTv4.root (for the reconstructed events) and the MiniMC file testGene-2016-Q2Bin-[Q2Bin].root (for the generated eventst produced by testGene program);
	    
		- produces the output file testGoofitEffi3DB0-2016-InputHisto-Q2Bin-[Q2Bin]-Bins-25-25-25.root with histograms of the efficiency;
		   the generated and the reconstructed distributions.
		   
testEffi     <= Usage: ./testEffi     [Q2Bin]      [where QBin2=0,1,2,3,4,5,6,7,8]
	    
		- reads the file testGoofitEffi3DB0-2016-InputHisto-Q2Bin-[Q2Bin]-Bins-25-25-25.root;		   
	    
		- reads the efficiency coefficents for the Bernstein Polynomial from  ListParValues-2016-Q2Bin-[Q2Bin]-Bins-25-25-25-BernDeg-[max1]-[max2]-[max3]-integraBin.plo; 
	    
		- performs the closure test evaluating [miniMC generated events]xEfficiency;
	    
		- produces the output testEffiRooFit-2016-Q2Bin-[Q2Bin]-Bins-25-25-25-BernDeg-[max1]-[max2]-[max3]-integraBin.root with the canvas "ClosurePlots", where are stored the closure plot projections, and the canvas  "ProjEffiPlots", with the efficiency projections. 
		   
		   
classes RooAbsReal => 2 class of type RooAbsReal are provided: RooBernsteinEffi.cxx	for the efficiency, and RooGenePdf.cxx for the P-Wave model of the angular distribution.	             

 
to compile all the executables  && make dictionary for the RooBernsteinEffi RooGenePdf classes :
```
make all
```

to clean the directory, removing all the compiled objects :

```
make clean
```

to make just the dictionary for the class RooBernsteinEffi :
```

make dict2
```
to make just the dictionary for the class RooGenePdf :
```

make dict1
```

to make just the program to reproduce the histogram files [testEffi3DB0-2016-makeHisto] :
```

make hist
```

