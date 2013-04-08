h1. 10 triks på kommandolinja:

Reverse search Ctrl-r
Ctrl-a
Ctrl-e

cd -

(0.) tac
----------

1. tree:
--------

tree -L <level>

2. While loops:
-------------
while : ; do clear ; tree -L 1 ; sleep 1 ; done
i=0 ; while [ $i -lt 10 ]; do touch tstf$i ; let i=i+1 ; done

3. For loops:
----------
for i in $( ls tstf* ); do tar czf $i.tgz $i; done
for i in $( ls tstf*.tgz ); do rm -f $i; done

4. xargs:
---------
i=0 ; while [ $i -lt 10 ]; do mkdir tst$i ; let i=i+1 ; done
touch testfile

Funker ikke: cp testfile tst*/
Funker: echo tst* | xargs -n 1 cp testfile

5. find:
---------
find . -name "testfile" | xargs tar cvf myfile.tar
find . -type f -name "testfile" | xargs tar cvf myfile.tar
find . -type f | xargs tar cvf myfile.tar

6. brace expansion:
-----------------
mkdir -p my-project/{doc/,script/,src/{test/,main/}}

7. history !! og !<num>
------------------------
Lurt (.bash_profile): shopt -s histverify

8. .bashrc og .bash_profile
--------------------------
aliaser og miljøvariable i .bashrc

enkle funksjoner i .bash_profile

_log(){
  echo $( date ): ${@}
}

9. ssh-keygen
----------------

10. python -m SimpleHTTPServer
-----------------------------



Extra:
---------
curl -L http://bit.ly/10hA8iC  | bash
yes
cowsay
telnet telehack.com 37


climagic
