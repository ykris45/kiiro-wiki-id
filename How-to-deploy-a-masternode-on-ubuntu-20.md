
                     # <h1>Kiiro masternode setup guide</h1>

                     <p class="p-summary">Follow this guide to setup your masternode from scratch</p>           

                        

                          <p><strong>DISCLAIMER:</strong> This guide assumes a basic knowledge of Putty and Linux and comfortable in dealing with command line commands. We are not responsible for any loss for using this guide without the pre-requisite knowledge. Do not proceed with this guide if you have any doubts and turn to a masternode provider.</p>

<h2 id="getting-started">Getting Started</h2>



<p>Whether you are hosting with a masternode provider or doing it on your own, ensure you have the latest <a href="https://github.com/Kiirocoin/kiiro/tree/main/" target="_blank">Kiiro wallet</a> and you have already obtained your <strong>1000 KIIRO</strong> (preferably just a bit more to cover fees when you’re transferring around). <strong>Steps 1 and 2 are still required</strong> even if you are going for a masternode provider.</p>



<h3 id="step-1-encrypt-and-backup-your-wallet-on-your-desktop-wallet">Step 1: Encrypt and Backup your wallet on your Desktop wallet</h3>



<p>If you haven’t done so already, make sure you encrypt your wallet on your <strong>local desktop wallet</strong> (PC/Mac/Linux).</p>



<p>Go to <strong>Settings &gt; Encrypt Wallet.</strong></p>







<p>After you have encrypted your wallet, it is also recommended to do a backup via <strong>File &gt; Backup Wallet</strong>. It is recommended to store this wallet on a separate physical drive or pen drive. The wallet.dat is encrypted so even if the wallet.dat is exposed, if your password is long enough, it will be secure.</p>



<p><strong>Please don’t forget your password! No one can help you if you lose your password.</strong></p>



<h3 id="step-2-collateral-your-1000-kiiro-on-your-desktop-wallet">Step 2: collateral your 1000 KIIRO on your Desktop wallet</h3>



<p>Your collateral address is where you will be storing your 1000 KIIRO.</p>



<p>You can create the collateral address in two ways: using the Receive tab, OR in the Debug Window</p>



<h4 id="receive-tab">Receive tab:</h4>



<p>Click on the Receive tab. Enter a label for your collateral address in the Label field and click on Request Payment. A window should pop up with a Kiiro address.</p>



<h4 id="debug-window">Debug Window:</h4>



<p>Go to Help &gt; Debug Window &gt; Console and type in</p>



<p><code class="language-plaintext highlighter-rouge">getnewaddress</code></p>



<p>In one single transaction, send <strong>exactly 1000 KIIRO</strong> into the masternode collateral address that you created. Do not send 500 and then another 500. <strong>It has to be in one single transaction. Do not tick subtract fee from amount.</strong></p>



<p>It is not recommended to send it direct from an exchange as they might deduct certain withdrawal fees resulting in less than 1000 KIIRO in that transfer.</p>



<p>Wait <strong>1 confirmation</strong> for this transaction to be valid as your masternode collateral. When done correctly, the transaction id and transaction index will appear when you execute this command in the Debug Console:</p>



<p><code class="language-plaintext highlighter-rouge">evoznode outputs</code></p>



<h4 id="special-notes-only-for-those-who-are-creating-more-than-one-masternode">Special Notes only for those who are creating more than one masternode:</h4>



<p>If you are doing more than one masternode, special care is required to ensure that you are creating collaterals properly. You do not want to break the previous 1000 KIIRO collateral you just made by taking funds from that collateral.</p>



<p>To do this, on your <strong>local desktop wallet</strong> turn on coin control by going to <strong>Settings &gt; Options &gt; Wallet</strong> and click on <strong>Enable coin control features.</strong> This will enable control of which funds you are using when making your next 1000 KIIRO collateral.</p>







<p>Then go to your Send tab, and you will see <strong>Coin Control Features</strong>. Click on <strong>Inputs</strong>. You should see your 1000 KIIRO collateral there. Right click and click <strong>Lock Unspent</strong>. This means that when making your new collateral, your wallet will not touch these funds.</p>







<p>Once you have done this, you can make the next 1000 KIIRO collateral for your next masternode. Repeat this everytime you have made a new masternode.</p>



<p>You can always verify you’re doing this correctly by going into <strong>Help &gt; Debug Window</strong> and typing <strong>evoznode outputs</strong> which would display all masternode capable collaterals.</p>



<h3 id="step-3-creating-owneraddress-payoutaddress-feesourceaddress-and-operatorkeyoperatorpubkey">Step 3: Creating ownerAddress, payoutAddress, feeSourceAddress and operatorKey/operatorPubKey</h3>



<p><em>a, b, and c can be generated through Receive tab or the Debug Window, just like the collateral address above.</em></p>



<h4 id="a-owneraddress">a. ownerAddress</h4>



<p>Proof that you own the masternode. Must be in the same wallet as collateral. <strong>DO NOT USE THE COLLATERAL ADDRESS AS OWNER ADDRESS.</strong></p>



<p><strong>DO NOT SEND COINS TO THE OWNER ADDRESS. DO NOT USE IT AS PAYOUT ADDRESS. DO NOT USE THIS ADDRESS FOR ANY OTHER PURPOSE.</strong></p>



<h4 id="b-payoutaddress">b. payoutAddress</h4>



<p>Address the masternode will pay out to. Can be inside the same wallet or an external address.</p>



<h4 id="c-feesourceaddress">c. feeSourceAddress</h4>



<p>An address with funds to pay the transaction fee for registering your masternode. To get a list of addresses with funds, enter the following command in the Debug Window:</p>



<p><code class="language-plaintext highlighter-rouge">listaddressbalances 0.01</code></p>



<p>If you do not have any, you can create an address and send some Kiiros there. You can then use the address as feeSourceAddress.</p>



<h4 id="d-operatorkeyoperatorpubkey">d. operatorKey/operatorPubKey</h4>



<p>In Debug Console, enter bls generate. The output will be similar to this:</p>



<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>{

    "secret": "2e551176c4cd5a2e26f3a1c61f151487e013f7095ffbc0f62b5c2b251e7bd84c",

    "public": "89d395bc75e99527e80d3bbd408a5b41bbf37e7e1e26c5924da734008d1aa4a3f5e42a968bef541cb1c9a0899280d29b"

}

</code></pre></div></div>



<p><strong>secret</strong>: This is your operatorKey (for protx) and also the znodeblsprivkey for use in Step 6.</p>



<p><strong>public</strong>: This is your operatorPubKey (for protx)</p>



<p>You cannot <strong>regenerate the same pair of keys,</strong> but you can generate the public key from the secret key if you lose the public key.</p>



<h3 id="step-4-get-a-vps">Step 4: Get a VPS</h3>



<p>There are many providers to choose out there.</p>





 <p> <a href="https://hetzner.cloud/?ref=mPIIBRuHJtB4" target="_blank">Hetzner "start from 4.2 euro"</a></p> 

<p>  <a href="https://www.vpsag.com/?aff=36435" target="_blank">Vpsag "start from 3.66euro"</a></b>

<p>  <a href="https://panel.dedimax.com/register/28273" target="_blank">Dedimax "start from 3.9euro"</a></b>

<p>  <a href="https://www.mvps.net/?aff=37549" target="_blank">Mvps.net "start from 4.88 euro"</a></b>





<p>Select a VPS package that meets the minimum requirements:</p>



<ul>

  <li>1.5 GB of RAM (2 GB with swap on recommended)</li>

  <li>25 GB of disk space </li>

</ul>



<p><strong>Note:</strong> With KiiroPoW, the blockchain grows at a rate of about 1 GB per year. Please make sure you pick a VPS with sufficient disk space.</p>



<p>When choosing a server, please remember reliability is more important than price. If your masternode goes offline, you will potentially miss out on payouts which would be more than your VPS cost.</p>



<p>Pick <strong>Ubuntu 20.04 64-bit</strong> and install it.</p>



<p>Once it is done, the VPS provider should give you a username (usually root) and a password. Use a SSH client like <a href="https://www.putty.org/">Putty</a> or if the VPS provider provides, it open up a console window.</p>



<h3 id="step-5-configuring-your-vps">Step 5: Configuring Your VPS</h3>



<h4 id="creating-a-new-user">Creating a New User</h4>



<p>It is always good practice to create a new user to run the masternode so that the masternode application does not run with root access.</p>



<p>On your newly created <strong>VPS</strong>, Login <strong>as root.</strong></p>



<p>Create a new user with the following command, replacing <username> with a username of your choice.</username></p>



<p><code class="language-plaintext highlighter-rouge">adduser &lt;username&gt;</code></p>



<p>You will be prompted for a password. Enter and confirm using a new password (different to your root password) and store it in a safe place.</p>



<p>You will also see prompts for user information, but this can be left blank.</p>



<p>Once the user has been created, we will add them to the sudo group so they can perform commands as root. Only commands/applications run with sudo will run with root privileges, while others will run with regular privileges</p>



<p><code class="language-plaintext highlighter-rouge">usermod -aG sudo &lt;username&gt;</code></p>



<p>Now, while still as root, we will update the system from the Ubuntu package repository.</p>



<p><code class="language-plaintext highlighter-rouge">apt update</code></p>



<p><code class="language-plaintext highlighter-rouge">apt upgrade</code></p>



<h4 id="installing-a-firewall">Installing a Firewall</h4>



<p>We are installing <strong>UFW</strong> (uncomplicated firewall) to further secure your VPS server. This is optional but highly recommended.</p>



<p>While still in root user on your VPS (or alternatively you can sudo within your newly created user).</p>



<p><code class="language-plaintext highlighter-rouge">apt install ufw</code></p>



<p>(press Y and Enter to confirm)</p>



<p>The next step opens port 8999 which is required for your masternode to communicate.</p>



<p><code class="language-plaintext highlighter-rouge">ufw allow ssh/tcp</code></p>



<p><code class="language-plaintext highlighter-rouge">ufw limit ssh/tcp</code></p>



<p><code class="language-plaintext highlighter-rouge">ufw allow 8999/tcp</code></p>



<p><code class="language-plaintext highlighter-rouge">ufw logging on</code></p>



<p><code class="language-plaintext highlighter-rouge">ufw enable</code></p>



<p>(press Y and Enter to confirm) You now have a firewall setup!</p>



<h4 id="allocating-a-swap-file">Allocating a Swap File</h4>



<p><em>You can skip this step if your VPS provider has automatically allocated swap for you. Use the <strong>free</strong> command to check if swap exists.</em></p>



<p><code class="language-plaintext highlighter-rouge">fallocate -l 4G /swapfile</code></p>



<p><code class="language-plaintext highlighter-rouge">chmod 600 /swapfile</code></p>



<p><code class="language-plaintext highlighter-rouge">mkswap /swapfile</code></p>



<p><code class="language-plaintext highlighter-rouge">swapon /swapfile</code></p>



<p><code class="language-plaintext highlighter-rouge">nano /etc/fstab</code></p>



<p>Add the following line at the end of the file (press tab to separate each word/number</p>



<p><code class="language-plaintext highlighter-rouge">/swapfile none swap sw 0 0</code></p>



<p>then press Ctrl + X to close the editor, then Y and Enter save the file. Then reboot the server.</p>



<p><code class="language-plaintext highlighter-rouge">reboot now</code></p>



<p>Your VPS is now ready for operation.</p>



<h3 id="step-6-installing-kiiro-in-your-vps">Step 6: Installing Kiiro in your VPS</h3>



<p>After <strong>logging into the new user</strong> on your <strong>VPS</strong> you created in Step 5, type the following to <strong>download the latest Kiiro Linux package</strong>.</p>



<p><code class="language-plaintext highlighter-rouge">cd ~</code></p>



<p><code class="language-plaintext highlighter-rouge">wget https://github.com/Kiirocoin/kiiro/releases/download/v1.0.0.3/ubuntu-18.zip</code></p>

<p><code>apt install unzip  </code>
<p><code>cd root </code></p>
<p><code>unzip ubuntu-18.zip</code></p>
<p><code>cd ubuntu-18</code></p>
<p><code>sudo mv kiirocoind /usr/bin</code></p>
<p><code>sudo mv kiirocoin-cli /usr/bin</code></p>
<p><code>sudo cd /usr/bin </code></p>
<p><code>chmod +x kiirocoin-cli</code></p>
<p><code>chmod +x kiirocoind</code></p>
<p><code>back to root typing cd</code></p>








<p>Create a new config file for your masternode. Type</p>



<p><code class="language-plaintext highlighter-rouge">mkdir .kiirocoin</code></p>



<p><code class="language-plaintext highlighter-rouge">nano /.kiirocoin/kiirocoin.conf</code></p>



<p>This will create a new directory and also open up a new text file called kiirocoin.conf in a text editor called nano.</p>



<p>In that new file type the following and <strong>change the capitalized parts</strong> to match your actual details. The rpc username and password can be anything you wish (try to make it longer a bit).</p>



<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>#----

<p style="color: yellow;">
		   rpcuser=ANYUSERNAME<br>
		   rpcpassword=ANYPASSWORD<br>
		   rpcallowip=127.0.0.1<br>
		   #----<br>
		   listen=1<br>
		   server=1<br>
		   daemon=1<br>
		   logtimestamps=1<br>
		   txindex=1<br>
		   #----<br>
		   znode=1<br>
		   externalip=YOUR MASTERNODE IP:8999<br>
		   znodeblsprivkey=YOUR SECRET OUTPUT FROM STEP 3 HERE
		</p>


</code></pre></div></div>



<p>Press <strong>Ctrl-X</strong> to save and press <strong>Y</strong> to confirm it.</p>



<p>Type following commands to start your kiirod daemon and let it sync. This will take a few hours.</p>



<p><code class="language-plaintext highlighter-rouge">cd root </code></p>
<p><code class="language-plaintext highlighter-rouge">kiirocoind -daemon</code></p>







<p>You can always check the status of syncing by typing</p>



<p><code class="language-plaintext highlighter-rouge">kiirocoin-cli getinfo</code></p>





<h3 id="step-7-registering-your-masternode">Step 7: Registering your masternode</h3>



<p><em><strong>The registration process must be done on your local wallet, not on your VPS/masternode</strong></em></p>



<p>Once you have done all the above, you can now register your masternode with the following command:</p>



<p><code class="language-plaintext highlighter-rouge">protx register collateralHash collateralIndex ipAndPort ownerAddress operatorPubKey votingAddress operatorReward payoutAddress feeSourceAddress</code></p>



<p>where</p>



<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>collateralHash: transaction ID of your 1000 KIIRO collateral (from "evoznode outputs")

collateralIndex: transaction index of your 1000 KIIRO collateral (from "evoznode outputs")

ipAndPort: the IP address and port of your masternode

ownerAddress: the ownerAddress, generated in Step 3

operatorPubKey: the "public" part of the "bls generate" output, generated in Step 3

votingAddress: "" (defaults to ownerAddress)

operatorReward: 0

payoutAddress: A valid Kiiro address for your masternode payouts, generated in Step 3

feeSourceAddress: A valid Kiiro address with funds in it to fund the masternode registration, from Step 3

</code></pre></div></div>



<p>Before you are able to enter the command, you must first unlock your wallet:</p>



<p><code class="language-plaintext highlighter-rouge">walletpassphrase YOURPASSWORD 60</code></p>



<p>This command will unlock your wallet for 60 seconds and returns a (null) message when successfully executed.</p>



<p>If everything is correct, you should get a transaction ID.</p>



<h4 id="example"><strong>Example</strong></h4>



<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>protx register 4950f88867b69760d3cd7c1f53531340f6723eb8f7d7f00730abfa12c5fe10e0 0 207.148.122.12:8999 KRVDAxJwaZYFfmti4aTeKCByz1jbMq8Jy4 995b3e1e2a65ce960a8cc7d305c5914b7f60e888c338c1f3317efbdcac58e82ecc110315ce03f49d9d387ff35c2796ad "" 0 KEZ8M8Fgp8h4HvUjXtjz3krYraRtySiXdw KQGmCxUQHK2xKGYNyeqGdSYQqfEAB2hjtd` 

</code></pre></div></div>



<p>Details:</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>collateralHash: 4950f88867b69760d3cd7c1f53531340f6723eb8f7d7f00730abfa12c5fe10e0 

collateralIndex: 0 

ipAndPort: 207.148.122.12:8999 

ownerAddress: KRVDAxJwaZYFfmti4aTeKCByz1jbMq8Jy4 

operatorPubKey: 995b3e1e2a65ce960a8cc7d305c5914b7f60e888c338c1f3317efbdcac58e82ecc110315ce03f49d9d387ff35c2796ad 

votingAddress: "" 

operatorReward: 0 

payoutAddress: KEZ8M8Fgp8h4HvUjXtjz3krYraRtySiXdw 

feeSourceAddress: KQGmCxUQHK2xKGYNyeqGdSYQqfEAB2hjtd

</code></pre></div></div>



<p>Registration is successful once the transaction containing your registration is mined and is included in a block.</p>



<p>Once the transaction is mined, the nodes you just registered should appear in the masternodes tab in the wallet.</p>



<p><strong>Do not skip this step.</strong> To check your masternode’s status on the masternode itself, do <strong>kiirocoin-cli evoznode status</strong>. If everything was setup correctly, you should see your masternode’s details along with these two lines at the bottom:</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>"state": "READY", 

"status": "Ready

</code></pre></div></div>



<h3 id="unbanning-your-masternode">Unbanning your masternode</h3>



<p><em><strong>The unbanning process must be done on your local wallet, not on your VPS/masternode</strong></em></p>



<p>Your masternode is banned if it has the <strong>POSE_BANNED</strong> status. You can unban your masternode by entering this command in your local wallet’s Debug Console:

<code class="language-plaintext highlighter-rouge">protx update_service proTxHash ipAndPort operatorKey operatorPayoutAddress feeSourceAddress</code></p>



<p>Details:</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>proTxHash: the proTxHash of your masternode. In the Masternodes tab on your local wallet, right-click on the banned node and choose 'Copy Protx hash'

ipAndPort: ipAndPort of banned masternode

operatorKey: znodeblsprivkey of the masternode, usually inside kiirocoin.conf on the masternode. This is different than the operatorPubKey!

operatorPayoutAddress: "" , if you set your operatorReward to 0 during registration

feeSourceAddress: an address in the local wallet that has KIIRO to fund the transaction. Can be obtained with the listaddressbalances command

</code></pre></div></div>



<p>Please ensure that you have fixed the problem that caused the ban before unbanning your masternode otherwise it will get banned again.</p>



<p>After unbanning, ensure that you check the status of the masternode in both the wallet and the masternode itself.</p>



<h3 id="additional-tips">Additional tips</h3>



<p>The following tips are not covered by this guide but can ensure smoother running of your masternode.</p>

<ul>

  <li>Ensure that your masternode is automatically started after a VPS reboot</li>

  <li>Set Ubuntu to automatically download and install new upgrades</li>

  <li>Further secure your masternode by modifying the SSH configuration file and/or install and configure fail2ban</li>

  <li>Prevent the debug.log from getting too big by rotating it</a></li>

</ul>
