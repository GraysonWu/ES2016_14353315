# lab1

## Install DOL in Ubuntu 14.04 

* ##INFO
**Distributed Operation Layer :** 
The distributed operation layer (DOL) is a software development framework to program parallel applications. The DOL allows to specify applications based on the Kahn process network model of computation and features a simulation engine based on SystemC. Moreover, the DOL provides an XML-based specification format to describe the implementation of a parallel application on a multi-processor systems, including binding and mapping.

    [learn more](www.tik.ee.ethz.ch/~shapes/dol.html)


* ##Install Essential Environment
`$	sudo apt-get update`
`$	sudo apt-get install ant`
`$ 	sudo apt-get install openjdk-7-jdk`
`$	sudo apt-get install unzip`

* ##Download Files
**Excute in a folder you like**
`$	sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz`
`$	sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip`
**DONE**
![ES1](http://image18-c.poco.cn/mypoco/myphoto/20161008/17/18362474920161008175326014.png?267x33_130)

* ##Unzip Files
**Excute in a folder you won't forget**

1. **New a folder named dol**
  `$	mkdir dol`

2. **Unzip dolethz.zip into dol**
  `$	unzip dol_ethz.zip -d dol`

3. **Unzip systemc-2.3.1.tgz**
  `$	tar -zxvf systemc-2.3.1.tgz`
**DONE**
![ES2](http://image18-c.poco.cn/mypoco/myphoto/20161008/17/18362474920161008175123076.png?436x35_130)

* ##Compile Systemc

1. **Change directory to systemc-2.3.1**
  `$	cd systemc-2.3.1`

2. **New a temporary folder named objdir**
  `$	mkdir objdir`

3. **Change directory to objdir**
  `$	cd objdir`

4. **Excute configure**
  `$	../configure CXX=g++ --disable-async-updates`
  And if you see this you should be happy
  ![res](http://image18-c.poco.cn/mypoco/myphoto/20161008/17/18362474920161008173020015.png?569x201_130)
  
5. **Compile**
  `$	sudo make install`
  `$    cd ..`
  `$    ls`
  You are supposed to see this
  ![folder](http://image18-c.poco.cn/mypoco/myphoto/20161008/17/18362474920161008173249097.png?596x63_130)
  you can see *include* & *lib-linux64* or *lib-linux*(it's depend on your OS)

6. **Print work directory**
  `$    pwd`
  ![dir](http://image18-c.poco.cn/mypoco/myphoto/20161008/17/18362474920161008173335047.png?389x33_130)
  Mark this down it will be useful later

* ##Compile DOL

1. **Change directory to dol**
  `$	cd ../dol`
2. **Edit build_zip.xml**
  Find the sentence below and change *YYY* to *pwd* that we marked before.
  `<property name="systemc.inc" value="YYY/include"/>`
  `<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>`
   **eg**: For me it was ↓
  ![xml](http://image18-c.poco.cn/mypoco/myphoto/20161008/18/18362474920161008181008098.png?785x44_130)

  
3. **Compile DOL**
  `$	ant -f build_zip.xml all`
  If you see this you should be happy
  ![compiledol](http://image18-c.poco.cn/mypoco/myphoto/20161008/19/1836247492016100819494504.png?597x496_130)

4. **Run example**
  `$    build/bin/main`
  `$	ant -f runexample.xml -Dnumber=1`
  If you see this you can shutdown your PC and have a rest.
  ![ex](http://image18-c.poco.cn/mypoco/myphoto/20161008/20/18362474920161008200408078.png?407x434_130)


   