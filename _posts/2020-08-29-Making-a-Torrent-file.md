---
layout: post
title: Making a Torrent file
---

I use the package ```transmission-create```, available with ```transmission-cli```.
I don't use ```mktorrent``` because ```transmission-create``` automatically choose the best conf for size piece.

Because I create a lot of torrent, I did a script available [here](https://github.com/Subarashii-no-Fansub/Torrent/).

You just have to:

1. Clone the repo
2. Open a console, here where you clone the repo, and execute ```chmod +x PublicTorrent.sh && chmod +x PrivateTorrent.sh```
3. Modify ```configTorrent.cfg```
	* ```setdirectory``` is where to put the .torrent in your computer
	* You must to set the two public tracker (```public_tracker_un```, ```public_tracker_deux``` and ```public_tracker_trois```).<br>Here good tracker you can use:
		* ```http://nyaa.tracker.wf:7777/announce``` (you must to registrer your torrent)
		* ```http://anidex.moe:6969/announce``` (you must to registrer your torrent)
		* ```udp://tracker.moeking.me:6969/announce```
		* and others that you can find [here](https://github.com/ngosang/trackerslist)
	* You must to set the private tracker (```private_tracker```).<br>Private tracker means disallow DHT and PeerExchange
	* Run ```$ ./PublicTracker 'myfile'``` or ```$ ./PublicTracker 'myfolder'```
	* Upload your torrent somewhere and add it to your bittorrent software to seed your file (your file must be completed download on your site/you must have the file to seed it)
	* And it's done :-)

## The bittorrent software I use

My favorites are ```transmission-bt``` (or simply ```transmission```) and ```qbittorrent```.

## The best conf for size piece

If you have to config it, here the best conf to choose your piece size; transmission is only compatible with max-size pieces of 2MiB, while qbitorrent can create up to 32MiB (but 16MiB is the max I recommend)
<table>
	<tr>
		<th>Total size of files</th>
		<th>Piece size to choose</th>
		<th>Equivalent for mktorrent args</th>
	</tr>
	<tr>
		<td>up to 50MiB</td>
		<td>32KiB</td>
		<td>-l 15</td>
	</tr>
	<tr>
		<td>50MiB to 150MiB</td>
		<td>64KiB</td>
		<td>-l 16</td>
	</tr>
	<tr>
		<td>150MiB to 350MiB</td>
		<td>128KiB</td>
		<td>-l 17</td>
	</tr>
	<tr>
		<td>350MiB to 512MiB</td>
		<td>256KiB</td>
		<td>-l 18</td>
	</tr>
	<tr>
		<td>512MiB to 1.0GiB</td>
		<td>512KiB</td>
		<td>-l 19</td>
	</tr>
	<tr>
		<td>1.0GiB to 2.0GiB</td>
		<td>1024KiB</td>
		<td>-l 20</td>
	</tr>
	<tr>
		<td>2.0GiB and up</td>
		<td>2048KiB</td>
		<td>-l 21</td>
	</tr>
</table>
