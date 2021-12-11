# log4j-fuzz-head-poc
针对 log4j批量fuzzz 头检测poc


使用
/nuclei -t log4j-fuzz-head-poc.yaml -u http://www.test.com  -o res.txt 单个
/nuclei -t log4j-fuzz-head-poc.yaml -l urls.txt  -o res.txt  批量
![image](https://user-images.githubusercontent.com/50769953/145665694-21632dd2-7336-474b-80ed-9cdba4919898.png)

