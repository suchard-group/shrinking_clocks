# Shrinkage-based random local clocks with scalable inference

This document outlines the steps necessary to recreate the analyses of *Shrinkage-based random local clocks with scalable inference*

## Setting up BEAST:
1. Ensure you have Java version 1.8 or later installed.
	* From the command line, type `java -version`.
	* The output should start with `java version "1.8.0_<other numbers>"`.
	* If java is not installed or the wrong version of java is installed, please follow the instructions [here](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).
2. Ensure you have `git` installed.
	* From the command line, type `git --version`. The version of git should be returned.
	* If `git` is not installed, please follow the instructions [here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
3. Ensure you have `ant` installed.
	* From the command line, type `ant -version`. The version of ant should be returned.
	* If `ant` is not installed, please follow the instructions [here](https://ant.apache.org/manual/install.html).
4. Download and build BEAST
	* Enter the following on the command line. 
```
git clone https://github.com/beast-dev/beast-mcmc.git
cd beast-mcmc
git checkout hmc-clock
ant
```

## Setting up the BEAGLE library:
* Clone and build the beagle library (see [https://github.com/beagle-dev/beagle-lib](https://github.com/beagle-dev/beagle-lib) for reference)
```
git clone https://github.com/beagle-dev/beagle-lib.git
cd beagle-lib
git checkout hmc-clock
./autogen.sh
./configure
make install
```

Note where the beagle library installs (typically /usr/local/lib)

## Running a BEAST XML file:
1. Navigate to the directory with the `beast.jar` file.
	* From the `beast-mcmc` directory (see above), enter the following into the command line:
```
cd build/dist
```
2. Run an `.xml` file from the command line
		* Enter `java -jar -Djava.library.path=/usr/local/lib beast.jar path/to/your/file.xml`.
	* Note that `library.path` should point to install location of `libhmsbeagle*.so` files
	* BEAST should begin running on the command line.

	* The output `.log` file will be in the `./beast-mcmc/build/dist` directory.
3. Use Tracer to view the `.log` file.
	* Tracer installation and usage instructions can be found [here](http://beast.community/tracer).








