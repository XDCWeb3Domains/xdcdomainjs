Instructions for dApp integration with 3rd wallets that support XDC network such as: metamask, nabox, onto, dcent etc

First step you need to install:

For Nodejs: 
``
npm i xdc3
``

For web app

``
<script src="https://cdn.jsdelivr.net/npm/xdc3@1.3.13416/dist/web3.min.js"></script>
``

You need to read more walletconnect to can do work with dcent or wallets that support walletconnect
https://docs.walletconnect.com/1.0/quick-start/dapps/web3-provider

Step 2:

``
var adapters = ['metamask', 'xdcpay', 'nabox', 'dcent', ];
var connector;

if (adapter == 'metamask')
		{
			window.web3 = new Web3(ethereum);

			window.ethereum.on('chainChanged', () => {
				document.location.reload();
			});
				  
			window.ethereum.on('accountsChanged', () => {
				 document.location.reload();
			});
			await web3.eth.requestAccounts();
		}

		if (adapter == 'xdcpay'){
			window.web3 = new Web3(window.xdc);
		}
		
		if (adapter == 'nabox'){
			window.web3 = new Web3(window.NaboxWallet);
			await web3.eth.requestAccounts();
		}
		
		if (adapter == 'onto')
		{
			window.web3 = new Web3(window.onto);
			await web3obj.eth.requestAccounts();
		}
		
		if (adapter == 'dcent'){
			var WalletConnectProvider = window.WalletConnectProvider.default;
			connector = new WalletConnectProvider({
				  rpc: {
					50: "https://rpc.xinfin.network"
				  },
				  qrcodeModalOptions: {
					mobileLinks: [
					  "dcent"
					],
					desktopLinks: [
					  "dcent"
					]
				  }
			});
				
			await connector.enable();
			window.web3 = new Web3(connector);
		}
``

Hope it helps, and we'll update when there's an integration for new wallets.
Thanks!
