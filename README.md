To build the docker image, run the following in this directory:
```sh
docker build -t mybwa .
```
To create the BWA index for MT.fa:
```sh
docker run -v `pwd`:/tmp -w /tmp mybwa index MT.fa
```
To run BWA-MEM:
```sh
docker run -v `pwd`:/tmp -w /tmp mybwa mem MT.fa test.fq > test.sam
```
You can use pipe, too:
```sh
cat test.fq | docker run -v `pwd`:/tmp -w /tmp mybwa mem MT.fa /dev/stdin > test.sam
```
