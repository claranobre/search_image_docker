#!/bin/bash
sudo docker images -a --format='{{json .ID}}' > list.txt
sed -i 's/"//g' list.txt
for line in $(cat list.txt); do
	 sudo docker image inspect --format '{{json .GraphDriver.Data.MergedDir}}' $line
done
