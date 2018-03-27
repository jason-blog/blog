<table cellspacing="0" cellpadding="0" style="word-wrap:break-word;border-spacing:0px;empty-cells:show;table-layout:fixed;width:744px;color:#333333;font-family:微软雅黑, Arial, HELVETICA;font-size:12px;background-color:#FEFEFE;">
	<tbody style="word-wrap:break-word;">
		<tr style="word-wrap:break-word;">
			<td class="t_f" id="postmessage_107449300" style="word-wrap:break-word;margin:0px;padding:0px;color:#111111;font-size:14px;line-height:2;">
				exFAT很好，MAC、WIN都支持，还可以支持大硬盘和大文件 ，但它有一个问题，有时会很严重。<br style="word-wrap:break-word;" />
<br style="word-wrap:break-word;" />
如果你拿它存电影、音乐等，或者暴雪的游戏，都没关系，都是大文件。<br style="word-wrap:break-word;" />
如果你拿它存一堆小文件，每个不超过128K，问题就出现了。<br style="word-wrap:break-word;" />
<br style="word-wrap:break-word;" />
1T硬盘，一个分区——<br style="word-wrap:break-word;" />
NTFS每个簇4K，就是说你的文件要是10K，占三个簇，浪费2K。<br style="word-wrap:break-word;" />
				<table cellspacing="0" cellpadding="0" style="word-wrap:break-word;border-spacing:0px;empty-cells:show;table-layout:fixed;width:744px;color:#333333;font-family:微软雅黑, Arial, HELVETICA;font-size:12px;background-color:#FEFEFE;">
					<tbody style="word-wrap:break-word;">
						<tr style="word-wrap:break-word;">
							<td class="t_f" id="postmessage_107449300" style="word-wrap:break-word;margin:0px;padding:0px;color:#111111;font-size:14px;line-height:2;">
								exFAT很好，MAC、WIN都支持，还可以支持大硬盘和大文件 ，但它有一个问题，有时会很严重。<br style="word-wrap:break-word;" />
<br style="word-wrap:break-word;" />
如果你拿它存电影、音乐等，或者暴雪的游戏，都没关系，都是大文件。<br style="word-wrap:break-word;" />
如果你拿它存一堆小文件，每个不超过128K，问题就出现了。<br style="word-wrap:break-word;" />
<br style="word-wrap:break-word;" />
1T硬盘，一个分区——<br style="word-wrap:break-word;" />
NTFS每个簇4K，就是说你的文件要是10K，占三个簇，浪费2K。<br style="word-wrap:break-word;" />
exFAT每个簇256K，10K的文件占一个簇，浪费246K。<br style="word-wrap:break-word;" />
<br style="word-wrap:break-word;" />
我曾经在装的一个cygwin，4.8G。<br style="word-wrap:break-word;" />
在NTFS分区，占5.2G，还好。<br style="word-wrap:break-word;" />
在exFAT分区，大概占50G吧，因为多数文件都只有几十K甚至不到1K。<br style="word-wrap:break-word;" />
<br style="word-wrap:break-word;" />
在NTFS里只占不到400G的数据（各种文件，电影、游戏、文档、程序源文件等），移到exFAT都快600G了。<br style="word-wrap:break-word;" />
<br style="word-wrap:break-word;" />
<br style="word-wrap:break-word;" />
exFAT分区小于512G的话，每个簇128K，还稍微节约一点，所以可以分至少两个区，每个512G。<br style="word-wrap:break-word;" />
<br style="word-wrap:break-word;" />
一个NTFS，存放一堆小文件，或者变化不大的文件，可以用虚拟机里的WIN系统来修改。<br style="word-wrap:break-word;" />
另一个是exFAT，放大文件或经常修改的文件。<br style="word-wrap:break-word;" />
还有一个方案就是把一堆小文件弄成磁盘映像，DMG或ISO，只要装载了就可以直接用，但里面的内容不方便修改。存成压缩文件亦可，都不会显出exFAT的问题。
							</td>
						</tr>
					</tbody>
				</table>
每个簇256K，10K的文件占一个簇，浪费246K。<br style="word-wrap:break-word;" />
<br style="word-wrap:break-word;" />
我曾经在装的一个cygwin，4.8G。<br style="word-wrap:break-word;" />
在NTFS分区，占5.2G，还好。<br style="word-wrap:break-word;" />
在exFAT分区，大概占50G吧，因为多数文件都只有几十K甚至不到1K。<br style="word-wrap:break-word;" />
<br style="word-wrap:break-word;" />
在NTFS里只占不到400G的数据（各种文件，电影、游戏、文档、程序源文件等），移到exFAT都快600G了。<br style="word-wrap:break-word;" />
<br style="word-wrap:break-word;" />
<br style="word-wrap:break-word;" />
exFAT分区小于512G的话，每个簇128K，还稍微节约一点，所以可以分至少两个区，每个512G。<br style="word-wrap:break-word;" />
<br style="word-wrap:break-word;" />
一个NTFS，存放一堆小文件，或者变化不大的文件，可以用虚拟机里的WIN系统来修改。<br style="word-wrap:break-word;" />
另一个是exFAT，放大文件或经常修改的文件。<br style="word-wrap:break-word;" />
还有一个方案就是把一堆小文件弄成磁盘映像，DMG或ISO，只要装载了就可以直接用，但里面的内容不方便修改。存成压缩文件亦可，都不会显出exFAT的问题。
			</td>
		</tr>
	</tbody>
</table>