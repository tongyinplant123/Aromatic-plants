<img width="758" height="187" alt="image" src="https://github.com/user-attachments/assets/3825e73f-a262-4ade-b163-d33a9563d936" /># Aromatic-plants
查看文件 ls -lh
切换文件 cd ~
建立文件 mkdir 文件夹名 或者 mkdir -p data/orthofinder/Lilium_regale
删除文件 rm
解压文件 gunzip 文件名.gz
下载注释文件 wget --user-agent="Mozilla/5.0" "链接地址" -O 保存的文件名



创建文件夹 → 移动注释文件 → 解压 → 把解压后的文件放到对应物种文件夹：
# 1. 进入 data 目录
cd ~/data

# 2. 创建 orthofinder 主目录
mkdir -p orthofinder

# 3. 在 orthofinder 里面创建物种目录（比如 Lilium_regale）
mkdir -p orthofinder/Lilium_regale

# 4. 回到主目录（假设你的 lrv2.gff 和 lrv2_mc.fa.gz 在 ~ 下）
cd ~

# 5. 把下载好的两个文件移动到物种目录里
mv lrv2.gff lrv2_mc.fa.gz ~/data/orthofinder/Lilium_regale/

# 6. 进入物种目录
cd ~/data/orthofinder/Lilium_regale/

# 7. 解压 fasta 文件（保留压缩包）
gunzip -k lrv2_mc.fa.gz

# （如果想删除压缩包直接省空间）
# gunzip lrv2_mc.fa.gz




运行工作 
1.conda 里面创建环境或者用已有环境
2.conda env list可以查看已有环境
base（当前正在用的）
aromatic（你自己建的环境）
fangxiang_plant（好像是别人建在 /home/yuxuan/ 下的，你可能没权限写）

3.在环境里安装包 conda install -n aromatic -c bioconda gffread
 echo "用法: $0 install <环境名> <软件名>"
    else
      echo "在环境 $2 中安装 $3 ..."
      conda install -n $2 -c bioconda $3 -y

4.激活环境 conda activate aromatic
5.运行包 gffread lrv2.gff -g lrv2_mc.fa -x Lilium_regale_cds.fa -y Lilium_regale_proteins.fa
6.退回到base： conda deactivate

