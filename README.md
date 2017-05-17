# WSSwarmClient
		
Master App

<!DOCTYPE html>
<html>
<head>
	<!-- Swarms libs -->
	<script src="https://cdn.socket.io/socket.io-1.0.6.js"></script>
	<script src="https://rawgit.com/salboaie/WSSwarmClient/master/src/SwarmDebug.js"></script>
	<script src="https://rawgit.com/salboaie/WSSwarmClient/master/src/CommunicationService.js"></script>
	<script src="https://rawgit.com/salboaie/WSSwarmClient/master/src/SwarmClient.js"></script>
	<script src="https://rawgit.com/salboaie/WSSwarmClient/master/src/SwarmHub.js"></script>
	<!-- / Swarms libs -->
</head>
<body>
	<div >

		<!-- content -->
		<iframe id="app-content"></iframe>
		<!-- /content -->
		
	</div>

	<script type="application/javascript">

		var target = document.getElementsById("app-content");
		//target iframe is responsible to load child apps that need connection to the backend
		
		var swarmHubMaster = new SwarmHub(target.contentWindow);
		
		swarmHubMaster.initConnection(...);
		//from now on swarmHubMaster will be responsible to maintain the connection with the backend without any intervention from
		//the apps that are loaded into the iframe.
		
	</script>
</body>
</html>



Child App

<!DOCTYPE html>
<html>
<head>
	<!-- Swarms libs -->
	<script src="https://rawgit.com/salboaie/WSSwarmClient/master/src/SwarmDebug.js"></script>
	<script src="https://rawgit.com/salboaie/WSSwarmClient/master/src/CommunicationService.js"></script>
	<script src="https://rawgit.com/salboaie/WSSwarmClient/master/src/SwarmHubClient.js"></script>
	<!-- / Swarms libs -->
</head>
<body>

	<!-- content -->
	..
	<!-- /content -->


	<script type="application/javascript">
		var swarmHubClient = new SwarmHubClient();
		//from now on the app can start swarms and send them to the backend without managing the connection
		//swarmHubClient.startSwarm(...);
		
	</script>
</body>
</html>