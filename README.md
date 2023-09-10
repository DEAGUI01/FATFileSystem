<h1>FAT File System Lab</h1>


<h2>Description</h2>
In this lab I investigate common file systems utilized by Windows. It includes the following tasks:
- <b>Examining the FAT and NTFS File Systems</b> 
- <b>Using a hex Editor to Explore a FAT Partition</b>
- <b>Verifying and viewing forensic image details</b>
- <b>Analyzing a FAT Partition with Autopsy</b>
<br />


<h2>Software and Utilities Used</h2>
- <b>HxD Hex Editor</b>
<br />
- <b>Autopsy Forensic Browser</b>

<h2>Environments Used </h2>
- <b>Windows 7 Pro</b> 
<br />
- <b>Kali 2 Linux</b>


<h2>Lab Walkthrough:</h2>

<p align="center">

Log into Windows <br/>
<img src="https://i.imgur.com/7Zg5T5o.png" height="80%" width="80%" alt="Log into Windows"/>
<br />
<br />
Got to computer, select properties of FAT32 drive and NTFS drive, compare security tab and see that it's missing on the FAT32 drive<br/>
<img src="https://i.imgur.com/AMIFS7y.png" height="80%" width="80%" alt="Investigate FAT and NTFS drives"/>
<br />
<br />
Check the quote tab, this is where usage can be restricted for users, see that it's also missing on the FAT32 drive <br/>
<img src="https://i.imgur.com/LfslfA6.png" height="80%" width="80%" alt="check quota tab"/>
<br />
<br />
Use command prompt to convert FAT32 volume to NTFS  <br/>
<img src="https://i.imgur.com/3eFxcOf.png" height="80%" width="80%" alt="convert FAT32 to NTFS"/>
<br />
<br />
Change the Volume Label on the FAT32 drive to NTFS and verify that the security and quota tabs are now present <br/>
<img src="https://i.imgur.com/ss9fq0q.png" height="80%" width="80%" alt="change volume label"/>
<br />
<br />
Analyze boot code of DOS (Disk Operating System) based file structure (FAT32 image) <br/>
<img src="https://i.imgur.com/4qgvKs7.png" height="80%" width="80%" alt="analyze boot code"/>
<br />
<br />
Analyze the first partition, notice the first bite is 80, meaning is bootable. Move over 4 bytes and notice the value of 0C, this is the partition identifier, meaning it's a FAT32 partition set to LBA (Logical Block Addressing) mode addressing <br/>
<img src="https://i.imgur.com/18MPjjI.png" height="80%" width="80%" alt="analyze first partition"/>
<br />
<br />
Analyze the next 3 partitions, notice they are unused since it's all zeros. Notice the last 2 bytes is the MBR (Master Boot Record) signature, which in this case is 55 AA.  <br/>
<img src="https://i.imgur.com/sRH9EDt.png" height="80%" width="80%" alt="analyze next 3 partitions"/>
<br />
<br />
Log into Kali Linux <br/>
<img src="https://i.imgur.com/J5oK1zR.png" height="80%" width="80%" alt="log into Kali Linux"/>
<br />
<br />
Use the command line or leafpad to view the text file with the hash value of a forensic image <br/>
<img src="https://i.imgur.com/jbD5hRN.png" height="80%" width="80%" alt="view hash file of image"/>
<br />
<br />
Use md5sum on the image to check that the hash value matches the one we previously viewed on the text file <br/>
<img src="https://i.imgur.com/I1C4DlB.png" height="80%" width="80%" alt="check md5sum"/>
<br />
<br />
Use sha1sum on the image to check that the hash value matches the one we previously viewed on the text file <br/>
<img src="https://i.imgur.com/3WXwMmG.png" height="80%" width="80%" alt="check sha1sum"/>
<br />
<br />
Open Autopsy Forensic Browser <br/>
<img src="https://i.imgur.com/RX4Pcir.png" height="80%" width="80%" alt="Autopsy"/>
<br />
<br />
Go to link on browser and click new case <br/>
<img src="https://i.imgur.com/dVj3NrM.png" height="80%" width="80%" alt="new case"/>
<br />
<br />
Add a host <br/>
<img src="https://i.imgur.com/LkqgsUR.png" height="80%" width="80%" alt="add host"/>
<br />
<br />
Add image file<br/>
<img src="https://i.imgur.com/sZlffQE.png" height="80%" width="80%" alt="add image"/>
<br />
<br />
Click analyze<br/>
<img src="https://i.imgur.com/Y8UrONv.png" height="80%" width="80%" alt="analyze"/>
<br />
<br />
Select file analysis and notice the FAT1 and FAT2 records, as well as the MBR<br/>
<img src="https://i.imgur.com/qIyaAiH.png" height="80%" width="80%" alt="anylze files"/>


<h2>Conclusion </h2>
Working on this lab helped develop my understanding of the FAT and NTFS File Systems, as well as the use of forensic tools and procedures such as using hex editors to analyze / investigate a partition or hard drive and the correct procedure of verifying the integrity of an image file through it's hash value before starting to work on it. I also learned the basics of using a computer forensics platform like Autopsy Forensic Browser.
</p>


