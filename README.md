In this repo, `bwa` is a statically linked binary (i.e. linked with `gcc
-static`). To build a docker image, run the following in this directory:
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
cat test.fq | docker run -iv `pwd`:/tmp -w /tmp mybwa mem MT.fa /dev/stdin > test.sam
```
This github repo has also been linked to [lh3lh3/bwa][dh] at the Docker Hub.
You can use the following to get the docker image and run it:
```sh
docker pull lh3lh3/bwa
docker run -v `pwd`:/tmp -w /tmp lh3lh3/bwa index MT.fa
```
This image has no dependencies on any other images and is thus very small.

[dh]: https://registry.hub.docker.com/u/lh3lh3/bwa/
