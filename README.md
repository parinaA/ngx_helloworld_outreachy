# ngx_helloworld_outreachy
This is my version of hello world of an Nginx module. It prints the constant string "Hello world". 
The following steps need to be taken to compile the module with the source and run nginx and see the output of the module:
1.Install GCC an in ct is writtes in c:
  sudo apt install build-essential -y
2.Download the souce code of nginx and extract it:
  wget https://nginx.org/download/nginx-1.13.1.tar.gz && tar zxvf nginx-1.13.1.tar.gz
3.Download all Nginx dependencies and extract them:
  # PCRE version 4.4 - 8.40
    wget https://ftp.pcre.org/pub/pcre/pcre-8.40.tar.gz && tar xzvf pcre-8.40.tar.gz
  # zlib version 1.1.3 - 1.2.11
    wget http://www.zlib.net/zlib-1.2.11.tar.gz && tar xzvf zlib-1.2.11.tar.gz
  # OpenSSL version 1.0.2 - 1.1.0
    wget https://www.openssl.org/source/openssl-1.1.0f.tar.gz && tar xzvf openssl-1.1.0f.tar.gz
 4.Configure, compile and install 
   cd /path/to/file/nginx1.10.1  
  ./configure --add-module=/home/path/to/helloworld --with-cc-opt="-Wno-error"
  sudo make
  sudo make install
 5.cd to the directory where it is installed. Since it is compiled from source, the directory by default should be usr/local/nginx/sbin/
  cd usr/local/nginx/sbin/
 6.Open the conf file with an editor and add the following lines to it:
   nano /usr/local/nginx/conf/nginx.conf
   location = /hello {
  helloworld;
}
 
 7.The Nginx executable should be found here on ls
 8.Run the executable:
  sudo ./nginx
 9.Go to your browser and run localhost/hello to see the output 
