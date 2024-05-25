<h1>使用localhost架設pufferPanel</h1>
<style>
    body {
      background-color: #808080; /* 背景顏色 */
      font-family: Arial, sans-serif;
      color: #333; /* 文字顏色 */
      padding: 20px;
    }
    .container {
      background-color: #fff; /* 容器背景顏色 */
      border-radius: 10px;
      padding: 20px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1); /* 添加陰影效果 */
    }
    h1 {
      color: #007bff; /* 標題顏色 */
    }
    p {
      font-size: 16px;
    }
  </style>
允許使用以下支援系統架設: <br>
<div class="table-wrapper docutils container">
<table class="docutils align-default">
<thead>
<tr class="row-odd"><th class="head"><p>OS/Version</p></th>
<th class="head"><p>AMD64</p></th>
<th class="head"><p>ARM64</p></th>
<th class="head"><p>AMD32</p></th>
</tr>
</thead>
<tbody>
<tr class="row-even"><td><p>Ubuntu Focal (20.04)</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
</tr>
<tr class="row-odd"><td><p>Ubuntu Jammy (22.04)</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
</tr>
<tr class="row-even"><td><p>Ubuntu Noble (24.04)</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
</tr>
<tr class="row-odd"><td><p>Debian Buster (10)</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
</tr>
<tr class="row-even"><td><p>Debian Bullseye (11)</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
</tr>
<tr class="row-odd"><td><p>Raspbian Buster (10)</p></td>
<td><p>No</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="row-even"><td><p>Raspbian Bullseye (11)</p></td>
<td><p>No</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
</tr>
</tbody>
</table>
</div>
<br>

# 請使用以下端口
`8080`<br>
# 安裝
<h3>Ubuntu/Debian</h3><br>

```
curl -s https://packagecloud.io/install/repositories/pufferpanel/pufferpanel/script.deb.sh | sudo bash
sudo apt-get install pufferpanel
```
<h3>新增用戶</h3><br>
這很重要! 不然你無法使用<br>

```
sudo pufferpanel user add
```
你會看到
* Username
* Email
* Password
* Confirm Password
# 啟動pufferpanel
```
sudo systemctl enable --now pufferpanel
```
<hr>
<h3>Docker</h3><br>

```
mkdir -p /var/lib/pufferpanel
docker volume create pufferpanel-config
docker create --name pufferpanel -p 8080:8080 -p 5657:5657 -v pufferpanel-config:/etc/pufferpanel -v /var/lib/pufferpanel:/var/lib/pufferpanel -v /var/run/docker.sock:/var/run/docker.sock --restart=on-failure pufferpanel/pufferpanel:latest
docker start pufferpanel
docker exec -it pufferpanel /pufferpanel/pufferpanel user add
```
你會看到
* Username
* Email
* Password
* Confirm Password
# 安裝完成
恭喜你安裝完成!!<br>請在網站上寫
```
http://localhost:8080
```
有顯示登入畫面代表你成功了!<br>
請登入剛剛設定的帳號密碼.
# 如何建立伺服器?
* 點擊範本<br>
在右下角你會看到
![image](https://github.com/Tira-tw/hosting-server-docs/assets/64715639/58ac9047-5cb3-44db-85f5-6fb7f6fc7454) << 點擊
* 選擇你想要的版本
* 點擊匯入範本
* 點擊伺服器
  在右下角你會看到一個`+`
* 點擊+
* 選擇你想要的版本
* 點擊`使用這個範本`
* 隨便取一個伺服器名稱
* 點擊`下一個`
* 點擊`下一個`
* 啟用 `EULA Agreement (true/false)`
* 設定你想要給伺服器的記憶體容量 `Memory (MB)`<br>
如果不會GB換算MB , [點擊這個網站](https://www.unitconverters.net/data-storage/gb-to-mb.htm)
* Version
伺服器版本
* 點擊新增
* 點擊伺服器
* 點擊你剛剛建立的伺服器
* 點擊安裝
請等待10-30秒
* 點擊啟動<br>
如果有`Done` or `timings restart` 代表完成囉
* 點擊檔案
* 點擊plugins
* [下載playit](https://github.com/playit-cloud/playit-minecraft-plugin/releases/latest/download/playit-minecraft-plugin.jar)<br>
請注意只支援以下版本
```
spigot
paper
bukkit
```
下載好後回到你的面板網站<br>
* 點擊上傳
* 上傳`playit-minecraft-plugin.jar`
* 回到主控台
* 填寫
```
reload confirm
```
或者是重新啟動<br>
接下來主控台會顯示一個網站,大概像這樣<br>
```
https://playit.gg/claim/xxxxxxxxxxxxxxxx
```
貼到遊覽器上<br>
不要使用遊客登入!<br>
建立好後你會看到有一個類別叫做`Tunnel Type`<br>
選擇`Minecraft Java` or `Minecraft Bedrock`<br>
請不要選錯喔! , Java , Bedrock是不一樣的版本!
# 如何更改IP? (需要有自己的網域 , 如果沒有可以跟我申請!)
如果你覺得playit提供的IP太醜<br>
你可以使用SRV設定<br>
以下是我的設定
![image](https://github.com/Tira-tw/hosting-server-docs/assets/64715639/8cd6324c-da6d-4cdd-a396-9fc2e0e76d41) <br>
<hr>
Port (required)
* playit提供的Port , 在`Allocation (Shared IP)`可以看到Port: xxxx<br>
Target (required)
* playit提供的IP , 在`Allocation (Shared IP)`可以看到IP: xxx.ip.ply.gg<br>
設定好之後就可以遊玩了!!!<br>
感謝您的耐心閱讀<br>
Facebook : [Hỏi Huyền](https://www.facebook.com/Lun.twn/)<br>
Discord : [Server](https://discord.gg/pPJsvtMqA4)
