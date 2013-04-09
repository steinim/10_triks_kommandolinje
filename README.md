h1. 10 triks på kommandolinja:

Forberedelser:
mkdir -p my-project/{doc/,script/,src/{test/,main/{site1,site2,site3}}}
find . -name "site*" -type d | touch index.html

0. Gå gjennom følgende underveis:
-------------------------------
ctrl-r
ctrl-a
ctrl-e
cd -

1. Interactive rm:
-------------------

rm -R *

cowsay "oh no"

git checkout .

rm -Ri *

touch ./-i

rm -R *

2. brace expansion:
-------------------
mkdir -p my-project/{doc/,script/,src/{test/,main/{site1,site2,site3}}}

3. tree:
--------
tree
tree -L 3

4. while loops:
-------------
while : ; do clear ; tree ; sleep 1 ; done

i=1 ; while [ $i -lt 4 ]; do touch my-project/src/main/site$i/index$i.html ; let i=i+1 ; done
rm my-project/src/main/site*/index*.html

5. for loops:
----------
for i in $( seq 1 3 ); do touch my-project/src/main/site$i/index$i.html ; done

rm my-project/src/main/site*/index*.html

cd my-project/src/main/

cd -
cd -

for i in $( seq 1 3 ); do touch site$i/index.html ; done

for d in $( ls -d site* ); do tar czf $d.tgz $d ; done

tar tvf site1.tgz

for f in $( ls site*.tgz ); do rm -i $f; done

6. xargs:
---------
i=4 ; while [ $i -lt 10 ]; do mkdir site$i ; let i=i+1 ; done
echo "<html><head><title>HEI</title></head><body><h1>HEI VERDEN</h1></body></html>" > index.html

Funker ikke:
cp index.html site*/

Funker:
echo site* | xargs -n 1 cp index.html

7. find:
---------
find site* -name index.html | xargs rm

Ctrl-r:
echo site* | xargs -n 1 cp index.html

find . -type f | xargs tar cvf files.tar
tar tvf files.tar

8. history !! og !<num>
------------------------
history
!<number>
!!
Lurt (.bash_profile): shopt -s histverify

9. .bashrc og .bash_profile
--------------------------
aliaser og miljøvariable i .bashrc

enkle funksjoner i .bash_profile

_useJava() {
  export JAVA_HOME=$(/usr/libexec/java_home -v ${1} -d64)
}

_log(){
  echo $( date ): ${@}
}

java -version
_useJava 1.6
java -version

for f in $( ls site* ); do _log $f ; done

10. python -m SimpleHTTPServer
-----------------------------
echo site* | xargs -n 1 cp index.html
cd site1
python -m SimpleHTTPServer 8080
cd ..

for i in $( seq 1 9 ); do cd site$i ; eval "python -m SimpleHTTPServer 808$i &"  ; cd .. ; let i=i+1 ; done

ps -ef | grep SimpleHTTPServer | grep -v grep | awk '{print $2}' | xargs kill -9

cowsay "Takk skal dere ha"

Extra:
---------
curl -L http://bit.ly/10hA8iC  | bash
telnet telehack.com 37
