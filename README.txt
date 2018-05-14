For the latest information about Hadoop, please visit our website at:

   http://hadoop.apache.org/core/

and our wiki, at:

   http://wiki.apache.org/hadoop/

This distribution includes cryptographic software.  The country in 
which you currently reside may have restrictions on the import, 
possession, use, and/or re-export to another country, of 
encryption software.  BEFORE using any encryption software, please 
check your country's laws, regulations and policies concerning the
import, possession, or use, and re-export of encryption software, to 
see if this is permitted.  See <http://www.wassenaar.org/> for more
information.

The U.S. Government Department of Commerce, Bureau of Industry and
Security (BIS), has classified this software as Export Commodity 
Control Number (ECCN) 5D002.C.1, which includes information security
software using or performing cryptographic functions with asymmetric
algorithms.  The form and manner of this Apache Software Foundation
distribution makes it eligible for export under the License Exception
ENC Technology Software Unrestricted (TSU) exception (see the BIS 
Export Administration Regulations, Section 740.13) for both object 
code and source code.

The following provides more details on the included cryptographic
software:
  Hadoop Core uses the SSL libraries from the Jetty project written 
by mortbay.org.


Sandy's Guava Shading Notes - May, 2018 

I found a shading pom example on Maven Central:
https://repository.cloudera.com/content/repositories/releases/org/apache/hadoop/cloudera-guava/2.5.0-cdh5.2.3.4/cloudera-guava-2.5.0-cdh5.2.3.4.pom
for a different version of hadoop, but the same 11.0.2 version of guava. 

Then I downloaded the Hadoop src for 2.6.0-cdh5.5.1 from here: 
http://archive.cloudera.com/cdh5/cdh/5/hadoop-2.6.0-cdh5.5.1-src.tar.gz

The src is a maven project the build and packaging can be run like this: 
JAVA_HOME=/usr/lib/jvm/java-7-oracle mvn package -Pdist -DskipTests -Dtar

The build system requires java 7 and protoc 2.5.0.  I already had java 7, but I had to go build protoc from here: 
https://github.com/google/protobuf/releases/tag/v2.5.0


I worked the maven shading plugin in by hand, and added setTurnVersion.sh to sed in the 
updated version number. 

