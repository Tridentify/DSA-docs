# Bloxd Scripts
## Dodgeball
(Minified version)
```js
function getPlayerIdsFromTeam(e){_teamedPlayers=[];for(let t of api.getPlayerIds())api.getMoonstoneChestItemSlot(t,0).attributes.customAttributes.team===e&&_teamedPlayers.push(t);return _teamedPlayers}timer=0,showTextCount=500,onPlayerDropItem=(e,t,o,a,i,s,l)=>"preventDrop",onPlayerDamagingOtherPlayer=(e,t,o,a,i,s)=>{if("Snowball"!==a||api.getMoonstoneChestItemSlot(e,0).attributes.customAttributes.team===api.getMoonstoneChestItemSlot(t,0).attributes.customAttributes.team||null==api.getMoonstoneChestItemSlot(e,0).attributes.customAttributes.team||null==api.getMoonstoneChestItemSlot(t,0).attributes.customAttributes.team||api.getEntitiesInRect([81,4,74],[75,7,78]).includes(t)||api.getEntitiesInRect([116,4,137],[125,8,121]).includes(t))return"Dirt"===a&&api.getMoonstoneChestItemSlot(e,0).attributes.customAttributes.team===api.getMoonstoneChestItemSlot(t,0).attributes.customAttributes.team&&api.getEntitiesInRect([84,3,87],[72,5,84]).includes(t)?(api.setPosition(t,api.getPosition(e)),"preventDamage"):"preventDamage";{let o=api.getEntityName(e),a=api.getEntityName(t);api.sendMessage(e,"+1 Gold Coin for killing a player",{color:"lime"}),api.clearKillstreak(t);let i=api.getMoonstoneChestItemSlot(e,1).attributes.customAttributes.kills,s=api.getMoonstoneChestItemSlot(e,0).attributes.customAttributes.team;i+=1,api.setMoonstoneChestItemSlot(e,1,"Ice",1,{customAttributes:{kills:i}}),api.setTargetedPlayerSettingForEveryone(e,"lobbyLeaderboardValues",{team:s,kills:i},!0),api.broadcastMessage([{str:a,style:{color:api.getMoonstoneChestItemSlot(t,0).attributes.customAttributes.team}}," was hit by ",{str:o,style:{color:api.getMoonstoneChestItemSlot(e,0).attributes.customAttributes.team}},"!"]);let l=api.getPosition(t);if(api.applyHealthChange(t,-1e3,{lifeformId:e,withItem:"Snowball"},!0),api.forceRespawn(t,l),"Red"===api.getMoonstoneChestItemSlot(t,0).attributes.customAttributes.team){api.setPosition(t,82.5,3,85.5);for(let e of getPlayerIdsFromTeam("Red"))e!==t?api.sendMessage(e,"A teammate has been eliminated! Go to the elimination zone and punch them with your fist to bring them back in the game",{color:"coral"}):api.sendMessage(e,"You have been eliminated! Wait for another teammate to save you",{color:"coral"});let e=api.getEntitiesInRect([84,3,87],[72,5,84]);if(!0===getPlayerIdsFromTeam("Red").every((t=>e.includes(t)))){for(let e of api.getMobIds())api.despawnMob(e);for(let e of api.getPlayerIds())api.setClientOption(e,"middleTextUpper",[{str:"BLUE",style:{color:"blue"}}," team won!"]),api.sendMessage(e,[{str:"BLUE",style:{color:"blue"}}," team won!"]),api.sendMessage(e,"New game starting!"),showTextCount=0,api.clearKillstreak(e);for(let e of getPlayerIdsFromTeam("Blue"))api.setPosition(e,78.5,4,76.5),api.giveItem(e,"Gold Coin",10),api.sendMessage(e,"+10 Gold Coin for winning",{color:"lime"}),api.setMoonstoneChestItemSlot(e,0,"Dirt",1,{customAttributes:{team:null}}),api.setMoonstoneChestItemSlot(e,1,"Ice",1,{customAttributes:{kills:0}}),api.setTargetedPlayerSettingForEveryone(e,"lobbyLeaderboardValues",{team:"",kills:""},!0);for(let e of getPlayerIdsFromTeam("Red"))api.setPosition(e,78.5,4,76.5),api.setMoonstoneChestItemSlot(e,0,"Dirt",1,{customAttributes:{team:null}}),api.setMoonstoneChestItemSlot(e,1,"Ice",1,{customAttributes:{kills:0}}),api.setTargetedPlayerSettingForEveryone(e,"lobbyLeaderboardValues",{team:"",kills:""},!0)}}else{api.setPosition(t,74.5,3,85.5);for(let e of getPlayerIdsFromTeam("Blue"))e!==t?api.sendMessage(e,"A teammate has been eliminated! Go to the elimination zone and punch them with your fist to bring them back in the game",{color:"coral"}):api.sendMessage(e,"You have been eliminated! Wait for another teammate to save you",{color:"coral"});let e=api.getEntitiesInRect([84,3,87],[72,5,84]);if(!0===getPlayerIdsFromTeam("Blue").every((t=>e.includes(t)))){for(let e of api.getMobIds())api.despawnMob(e);for(let e of api.getPlayerIds())api.setClientOption(e,"middleTextUpper",[{str:"RED",style:{color:"red"}}," team won!"]),api.sendMessage(e,[{str:"RED",style:{color:"red"}}," team won!"]),api.sendMessage(e,"New game starting!"),showTextCount=0,api.clearKillstreak(e);for(let e of getPlayerIdsFromTeam("Blue"))api.setPosition(e,78.5,4,76.5),api.setMoonstoneChestItemSlot(e,0,"Dirt",1,{customAttributes:{team:null}}),api.setMoonstoneChestItemSlot(e,1,"Ice",1,{customAttributes:{kills:0}}),api.setTargetedPlayerSettingForEveryone(e,"lobbyLeaderboardValues",{team:"",kills:""},!0);for(let e of getPlayerIdsFromTeam("Red"))api.setPosition(e,78.5,4,76.5),api.giveItem(e,"Gold Coin",10),api.sendMessage(e,"+10 Gold Coin for winning",{color:"lime"}),api.setMoonstoneChestItemSlot(e,0,"Dirt",1,{customAttributes:{team:null}}),api.setMoonstoneChestItemSlot(e,1,"Ice",1,{customAttributes:{kills:0}}),api.setTargetedPlayerSettingForEveryone(e,"lobbyLeaderboardValues",{team:"",kills:""},!0)}}api.giveItem(e,"Gold Coin",1)}},tick=e=>{timer+=1,showTextCount+=1;for(let e of api.getPlayerIds())null==api.getMoonstoneChestItemSlot(e,0)&&(api.setMoonstoneChestItemSlot(e,0,"Dirt",1,{customAttributes:{team:null}}),api.setMoonstoneChestItemSlot(e,1,"Ice",1,{customAttributes:{kills:0}})),api.getEntitiesInRect([75,4,78],[81,7,74]).includes(e)||timer%200==0&&api.giveItem(e,"Snowball",1,{customDisplayName:"Dodgeball",customDescription:"Throw on other players of the other side to eliminate them!"}),null!=api.getMoonstoneChestItemSlot(e,0).attributes.customAttributes.team?api.setTargetedPlayerSettingForEveryone(e,"colorInLobbyLeaderboard",api.getMoonstoneChestItemSlot(e,0).attributes.customAttributes.team,!0):api.setTargetedPlayerSettingForEveryone(e,"colorInLobbyLeaderboard","black",!0);if(timer%1200==0&&(api.createItemDrop(95.5,3,87.5,"Gold Coin",1,!0,{}),api.createItemDrop(95.5,3,121.5,"Gold Coin",1,!0,{}),api.createItemDrop(61.5,3,87.5,"Gold Coin",1,!0,{}),api.createItemDrop(61.5,3,121.5,"Gold Coin",1,!0,{})),timer%400==0&&(api.createItemDrop(74.5,3,121.5,"Snowball",1,!0,{customDisplayName:"Dodgeball",customDescription:"Throw on other players of the other side to eliminate them!"}),api.createItemDrop(61.5,3,108.5,"Snowball",1,!0,{customDisplayName:"Dodgeball",customDescription:"Throw on other players of the other side to eliminate them!"}),api.createItemDrop(61.5,3,100.5,"Snowball",1,!0,{customDisplayName:"Dodgeball",customDescription:"Throw on other players of the other side to eliminate them!"}),api.createItemDrop(82.5,3,121.5,"Snowball",1,!0,{customDisplayName:"Dodgeball",customDescription:"Throw on other players of the other side to eliminate them!"}),api.createItemDrop(95.5,3,108.5,"Snowball",1,!0,{customDisplayName:"Dodgeball",customDescription:"Throw on other players of the other side to eliminate them!"}),api.createItemDrop(95.5,3,100.5,"Snowball",1,!0,{customDisplayName:"Dodgeball",customDescription:"Throw on other players of the other side to eliminate them!"})),100===showTextCount){for(let e of api.getPlayerIds())api.setClientOption(e,"middleTextUpper","");showTextCount=500}},onPlayerJoin=e=>{api.setWalkThroughRect(e, [78, 4, 83], [78, 4, 125], 0),api.setMoonstoneChestItemSlot(e,0,"Dirt",1,{customAttributes:{team:null}}),api.setMoonstoneChestItemSlot(e,1,"Ice",1,{customAttributes:{kills:0}}),api.setPosition(e,78.5,4,76.5),api.setClientOption(e,"lobbyLeaderboardInfo",{pfp:{sortPriority:1},name:{displayName:"Name",sortPriority:0},team:{displayName:"Team",sortPriority:0},kills:{displayName:"Kills",sortPriority:0}}),api.setClientOption(e,"maxAuraLevel",0),api.setClientOption(e,"cantChangeError",""),api.setClientOption(e,"cantBreakError",""),api.setClientOption(e,"cantBuildError",""),api.setClientOption(e,"droppedItemScale",3),api.setClientOption(e,"useFullInventory",!1),api.setClientOption(e,"canUseZoomKey",!1),api.setClientOption(e,"canCraft",!1),api.setTargetedPlayerSettingForEveryone(e,"lobbyLeaderboardValues",{team:"",kills:""},!0)},playerCommand=(e,t)=>"spawn"===t?(api.getEntitiesInRect([84,3,87],[72,5,84]).includes(e)?api.sendMessage(e,"You cannot teleport to spawn now",{color:"#CEF3FF"}):(api.setPosition(e,78.5,4,76.5),api.sendMessage(e,"Teleported to spawn",{color:"#CEF3FF"}),api.setMoonstoneChestItemSlot(e,0,"Dirt",1,{customAttributes:{team:null}}),api.setMoonstoneChestItemSlot(e,1,"Ice",1,{customAttributes:{kills:0}}),api.setTargetedPlayerSettingForEveryone(e,"lobbyLeaderboardValues",{team:"",kills:""},!0)),!0):"shop"===t&&(api.getEntitiesInRect([84,3,87],[72,5,84]).includes(e)?api.sendMessage(e,"You cannot teleport to the shop now",{color:"#CEF3FF"}):(api.setPosition(e,120.5,4,130),api.sendMessage(e,"Teleported to the shop",{color:"#CEF3FF"}),api.setMoonstoneChestItemSlot(e,0,"Dirt",1,{customAttributes:{team:null}}),api.setMoonstoneChestItemSlot(e,1,"Ice",1,{customAttributes:{kills:0}}),api.setTargetedPlayerSettingForEveryone(e,"lobbyLeaderboardValues",{team:"",kills:""},!0)),!0),onPlayerChat=(e,t,o)=>{if(null==api.getMoonstoneChestItemSlot(e,0).attributes.customAttributes.team||api.getEntitiesInRect([81,4,74],[75,7,78]).includes(e))return api.broadcastMessage([{str:api.getEntityName(e)+":",style:{color:"#CEF3FF"}}," ",t]),!1;{let o=api.getMoonstoneChestItemSlot(e,0).attributes.customAttributes.team;return api.broadcastMessage([{str:"["+o+"]",style:{color:o}}," ",{str:api.getEntityName(e)+":",style:{color:"#CEF3FF"}}," ",t]),!1}},onPlayerKilledMob=(e,t,o,a)=>"preventDrop",onWorldAttemptSpawnMob=(e,t,o,a)=>"preventSpawn",onPlayerAttemptSpawnMob=(e,t,o,a,i)=>{if(api.getEntitiesInRect([81,4,74],[75,7,78]).includes(e)||api.getEntitiesInRect([116,4,137],[125,8,121]).includes(e))return api.sendMessage(e,"You cannot spawn a mob here",{color:"#CEF3FF"}),api.giveItem(e,t+" Spawn Orb"),"preventSpawn";api.sendMessage(e,"Spawned a "+t,{color:"#CEF3FF"}),api.broadcastMessage([{str:api.getEntityName(e),style:{color:api.getMoonstoneChestItemSlot(e,0).attributes.customAttributes.team}}," has spawned a "+t+"!"])},onMobKilledPlayer=(e,t,o,a)=>{api.setMoonstoneChestItemSlot(t,0,"Dirt",1,{customAttributes:{team:null}}),api.setMoonstoneChestItemSlot(t,1,"Ice",1,{customAttributes:{kills:0}}),api.setTargetedPlayerSettingForEveryone(t,"lobbyLeaderboardValues",{team:"",kills:""},!0)},onPlayerLeave=(e,t)=>{let o=api.getMoonstoneChestItemSlot(e,0).attributes.customAttributes.team;if("Red"===o){let t=api.getEntitiesInRect([84,3,87],[72,5,84]),o=getPlayerIdsFromTeam("Red").filter((t=>t!==e));if(!0===o.every((e=>t.includes(e)))){for(let e of api.getMobIds())api.despawnMob(e);for(let e of api.getPlayerIds())api.setClientOption(e,"middleTextUpper",[{str:"BLUE",style:{color:"blue"}}," team won!"]),api.sendMessage(e,[{str:"BLUE",style:{color:"blue"}}," team won!"]),api.sendMessage(e,"New game starting!"),showTextCount=0,api.clearKillstreak(e);for(let e of getPlayerIdsFromTeam("Blue"))api.setPosition(e,78.5,4,76.5),api.giveItem(e,"Gold Coin",10),api.sendMessage(e,"+10 Gold Coin for winning",{color:"lime"}),api.setMoonstoneChestItemSlot(e,0,"Dirt",1,{customAttributes:{team:null}}),api.setMoonstoneChestItemSlot(e,1,"Ice",1,{customAttributes:{kills:0}}),api.setTargetedPlayerSettingForEveryone(e,"lobbyLeaderboardValues",{team:"",kills:""},!0);for(let e of o)api.setPosition(e,78.5,4,76.5),api.setMoonstoneChestItemSlot(e,0,"Dirt",1,{customAttributes:{team:null}}),api.setMoonstoneChestItemSlot(e,1,"Ice",1,{customAttributes:{kills:0}}),api.setTargetedPlayerSettingForEveryone(e,"lobbyLeaderboardValues",{team:"",kills:""},!0)}}else if("Blue"===o){let t=api.getEntitiesInRect([84,3,87],[72,5,84]),o=getPlayerIdsFromTeam("Blue").filter((t=>t!==e));if(!0===o.every((e=>t.includes(e)))){for(let e of api.getMobIds())api.despawnMob(e);for(let e of api.getPlayerIds())api.setClientOption(e,"middleTextUpper",[{str:"RED",style:{color:"red"}}," team won!"]),api.sendMessage(e,[{str:"RED",style:{color:"red"}}," team won!"]),api.sendMessage(e,"New game starting!"),showTextCount=0,api.clearKillstreak(e);for(let e of o)api.setPosition(e,78.5,4,76.5),api.setMoonstoneChestItemSlot(e,0,"Dirt",1,{customAttributes:{team:null}}),api.setMoonstoneChestItemSlot(e,1,"Ice",1,{customAttributes:{kills:0}}),api.setTargetedPlayerSettingForEveryone(e,"lobbyLeaderboardValues",{team:"",kills:""},!0);for(let e of getPlayerIdsFromTeam("Red"))api.setPosition(e,78.5,4,76.5),api.giveItem(e,"Gold Coin",10),api.sendMessage(e,"+10 Gold Coin for winning",{color:"lime"}),api.setMoonstoneChestItemSlot(e,0,"Dirt",1,{customAttributes:{team:null}}),api.setMoonstoneChestItemSlot(e,1,"Ice",1,{customAttributes:{kills:0}}),api.setTargetedPlayerSettingForEveryone(e,"lobbyLeaderboardValues",{team:"",kills:""},!0)}}};
```

## Freeze Tag
```js
let waitSeconds = 30
let playersRequired = 2
let showMsg = 5
let gameLength = 2
let lobFull = 7

resTimer = 50000
waitTimer = waitSeconds * 20 + 1
game = false
gameTimer = gameLength * 60 * 20 + 1
r1timer = 50000
newTime = 10000

function randPlayer() {
	let players = api.getPlayerIds()
	nonDead = []
	for (let pId of players) {
		if (api.isAlive(pId)) {
			nonDead.push(pId)
		}
	}
	if (nonDead.length > 1) {
		let rand = nonDead[Math.floor(Math.random() * nonDead.length)]
		return rand
	} else {
		return null
	}
}

tick = (ms) => {
	if (!game) {
		waitTimer -= 1
	}
	resTimer += 1
	r1timer += 1
	newTime += 1
	if (resTimer === 100) {
		resTimer = 50000
		for (let pId of api.getPlayerIds()) {
			api.setClientOption(pId, "middleTextUpper", "")
		}
	}
	if (resTimer === 1) {
		for (let pId of api.getPlayerIds()) {
			api.setClientOption(pId, "RightInfoText", [{str: "Freeze Tag ", style: {color: "lightblue", fontSize: "20px"}}, {icon: "Frozen", style: {fontSize: "30px"}}, "\nTagger: ", {str: api.getEntityName(player), style: {color: "lightblue"}}, "\nTime Left: ", {str: `${gameLength * 60}`, style: {color: "lime"}}])
		}
	}
	if (r1timer === 100) {
		for (let pId of api.getPlayerIds()) {
			api.setClientOption(pId, "middleTextUpper", "")
		}
		r1timer = 50000
	}
	if (newTime === 100) {
		for (let pId of api.getPlayerIds()) {
			api.setClientOption(pId, "middleTextUpper", "")
		}
	}
	if (!game) {
		if (waitTimer < 1) {
			for (let pId of api.getPlayerIds()) {
				waitTimer = waitSeconds * 20
			}
			if (api.getPlayerIds().length < playersRequired) {
				api.broadcastMessage(`Need ${playersRequired} or more players to start the game`, {color: "#CEF3FF"})
			} else {
				api.broadcastMessage("Game starting!", {color: "#CEF3FF"})
				player = randPlayer()
				if (player == null) {
					for (let pId of api.getPlayerIds()) {
						api.kickPlayer(pId, "You have been kicked for inactivity")
					}
				}
				for (let pId of api.getPlayerIds()) {
					api.setClientOption(pId, "middleTextUpper", "")
					api.setClientOption(pId, "RightInfoText", "")
					api.setWalkThroughType(pId, "Glass", true)
					api.setClientOption(pId, "middleTextLower", "")
					api.setClientOption(pId, "creative", false)
					api.setPosition(pId, [242, 80, 82])
					api.removeEffect(pId, "Rested Speed")
					api.removeEffect(pId, "Speed")
					api.applyEffect(pId, "Speed", 5000, {inbuiltLevel: 5})
					api.playSound(pId, "beep", 1, 2)
					api.setHealth(pId, 100)
					api.removeEffect(pId, "Invisible")
					api.setClientOption(pId, "useInventory", true)
					api.setClientOption(pId, "useFullInventory", false)
				}
				api.setTargetedPlayerSettingForEveryone(player, "hasPriorityNametag", true, false)
				api.setEveryoneSettingForPlayer(player, "hasPriorityNametag", true, false)
				api.setTargetedPlayerSettingForEveryone(player, "nameTagInfo", {
					backgroundColor: "lightblue"
				})
				game = true
				api.removeEffect(player, "Speed")
				api.applyEffect(player, "Speed", null, {inbuiltLevel: 1})
				api.applyEffect(player, "Frozen", 5000, {inbuiltLevel: 1})
				api.setPosition(player, [242, 74, 82])
				newTime = 0
				api.broadcastMessage(["The tagger is ", {str: api.getEntityName(player), style: {color: "lightblue"}}, "!"])
			}
		}
		if (waitTimer % 20 === 0) {
			for (let pId of api.getPlayerIds()) {
				api.setClientOption(pId, "RightInfoText", ["Game starting in ", {str: JSON.stringify(waitTimer / 20), style: {color: "lime"}}])
				api.setClientOption(pId, "middleTextUpper", "")
				if (waitTimer / 20 === 3) {
					api.setClientOption(pId, "middleTextUpper", ["Game starting in ", {str: "3", style: {color: "lime"}}])
					api.playSound(pId, "beep", 1, 3)
				} else if (waitTimer / 20 === 2) {
					api.setClientOption(pId, "middleTextUpper", ["Game starting in ", {str: "2", style: {color: "lime"}}])
					api.playSound(pId, "beep", 1, 3)
				} else if (waitTimer / 20 === 1) {
					api.setClientOption(pId, "middleTextUpper", ["Game starting in ", {str: "1", style: {color: "lime"}}])
					api.playSound(pId, "beep", 1, 3)
				}
			}
		}
	}
	if (game) {
		gameTimer -= 1
		if (gameTimer < 1) {
			game = false
			gameTimer = gameLength * 60 * 20 + 1
			api.broadcastMessage("Map changed to Abandoned City", {color: "#CEF3FF"})
			for (let pId of api.getPlayerIds()) {
				api.setClientOption(pId, "RightInfoText", ["Game starting in ", {str: `${waitSeconds}`, style: {color: "lime"}}])
				api.removeEffect(pId, "Frozen")
				api.setTargetedPlayerSettingForEveryone(pId, "nameTagInfo", {backgroundColor: ""})
				api.setHealth(pId, 0)
				api.setHealth(pId, 100)
				api.removeEffect(pId, "Rested Speed")
				api.removeEffect(pId, "Speed")
				api.setTargetedPlayerSettingForEveryone(pId, "hasPriorityNametag", false, false)
				api.setClientOption(pId, "useInventory", true)
				api.setClientOption(pId, "useFullInventory", false)
			}
			let rem = api.getPlayerIds().filter(pId => pId !== player)
			whoWin = 0
			invisPlayers = 0
			api.removeEffect(player, "Speed")
			for (let pId of rem) {
				if (!api.getEffects(pId).includes("Frozen") && !api.getEffects(pId).includes("Invisible")) {
					whoWin += 1
				} else if (api.getEffects(pId).includes("Invisible")) {
					invisPlayers += 1
				}
			}
			whoWin -= 1
			let runnerCount = api.getPlayerIds().length - 1
			runnerCount -= invisPlayers
			if (whoWin >= (runnerCount / 2)) {
				api.broadcastMessage("The runners won!", {color: "goldenrod"})
				for (let pId of api.getPlayerIds()) {
					api.setClientOption(pId, "middleTextUpper", "The runners won!")
				}
				for (let pId of rem) {
					api.giveItem(pId, "Gold Coin", 10)
					api.sendMessage(pId, "You won!")
				}
			} else {
				api.broadcastMessage(`The tagger (${api.getEntityName(player)}) won!`, {color: "goldenrod"})
				for (let pId of api.getPlayerIds()) {
					api.setClientOption(pId, "middleTextUpper", "The tagger won!")
				}
				api.giveItem(player, "Gold Coin", 10)
				api.sendMessage(player, "You won!")
			}
			r1timer = 0
		}
		if (gameTimer % 20 === 0) {
			for (let pId of api.getPlayerIds()) {
				api.setClientOption(pId, "RightInfoText", [{str: "Freeze Tag ", style: {color: "lightblue", fontSize: "20px"}}, {icon: "Frozen", style: {fontSize: "30px"}}, "\nTagger: ", {str: api.getEntityName(player), style: {color: "lightblue"}}, "\nTime Left: ", {str: `${gameTimer / 20}`, style: {color: "lime"}}])
			}
		}
	}
	for (let pId of api.getPlayerIds()) {
		let x = api.getPosition(pId)[0]
		let y = api.getPosition(pId)[1]
		let z = api.getPosition(pId)[2]
		if (y < 73 || z > 133.5 || z < 30.5 || x > 293.5 || x < 190.5) {
			api.setPosition(pId, [242, 80, 82])
		}
	}
}

onPlayerJoin = (pId) => {
	api.setClientOptions(pId, {
		RightInfoText: "",
		middleTextUpper: "",
		respawnButtonText: "Stay in Lobby",
		secsToRespawn: 3,
		usePlayAgainButton: true,
		useFullInventory: false,
		canUseZoomKey: true,
		canCraft: false,
		canChange: false,
		creative: false,
		maxAuraLevel: 0
	})
	api.setTargetedPlayerSettingForEveryone(pId, "nameTagInfo", {backgroundColor: ""})
	api.setPosition(pId, [242, 88, 82])
	let coins = api.getInventoryItemAmount(pId, "Gold Coin")
	api.clearInventory(pId)
	api.giveItem(pId, "Gold Coin", coins)
	if (game) {
		api.setPosition(pId, [242, 88, 82])
		api.setClientOption(pId, "middleTextLower", "You are spectating")
		api.setClientOption(pId, "creative", true)
		api.setWalkThroughType(pId, "Glass")
		api.setPosition(pId, [242, 88, 82])
		api.setHealth(pId, null)
		api.applyEffect(pId, "Invisible", null, {})
		api.setClientOption(pId, "useInventory", false)
		api.setClientOption(pId, "useFullInventory", false)
	} else {
		api.setPosition(pId, [242, 88, 82])
		api.setClientOption(pId, "middleTextLower", "")
		api.setClientOption(pId, "creative", false)
		api.setWalkThroughType(pId, "Glass", true)
		api.setPosition(pId, [242, 88, 82])
		api.setHealth(pId, 100)
		api.removeEffect(pId, "Invisible")
		if (api.getPlayerIds().length === lobFull && waitTimer > 320) {
			waitTimer = 15 * 20 + 1
		}
		api.setClientOption(pId, "useInventory", true)
		api.setClientOption(pId, "useFullInventory", false)
	}
}

onPlayerDamagingOtherPlayer = (atkId, dmgId, dmg, item, part, dmgDbId) => {
	if (game) {
		if (atkId === player && !api.getEffects(dmgId).includes("Frozen")) {
			api.applyEffect(dmgId, "Frozen", null, {})
			api.sendMessage(atkId, ["You have tagged ", {str: api.getEntityName(dmgId), style: {color: "lime"}}, "!"])
			api.sendMessage(dmgId, "You have been tagged by the tagger!", {color: "coral"})
			api.broadcastMessage(["The tagger has tagged ", {str: api.getEntityName(dmgId), style: {color: "lightblue"}}, "!"])
			others = api.getPlayerIds().filter(id => id !== player)
			invis = []
			for (let pId of api.getPlayerIds()) {
				if (api.getEffects(pId).includes("Invisible")) {
					invis.push(pId)
				}
			} 
			for (let pId of invis) {
				others = others.filter(id => id !== pId)
			}
			allFrozen = true
			for (let pId of others) {
				if (!api.getEffects(pId).includes("Frozen")) {
					allFrozen = false
				} else {
					continue
				}
			}
			if (allFrozen) {
				game = false
				gameTimer = gameLength * 60 * 20 + 1
				api.broadcastMessage("Map changed to Abandoned City", {color: "#CEF3FF"})
				for (let pId of api.getPlayerIds()) {
					api.setClientOption(pId, "RightInfoText", ["Game starting in ", {str: `${waitSeconds}`, style: {color: "lime"}}])
					api.removeEffect(pId, "Frozen")
					api.setTargetedPlayerSettingForEveryone(pId, "nameTagInfo", {backgroundColor: ""})
					api.setHealth(pId, 0)
					api.setHealth(pId, 100)
					api.removeEffect(pId, "Rested Speed")
					api.removeEffect(pId, "Speed")
					api.setTargetedPlayerSettingForEveryone(pId, "hasPriorityNametag", false, false)
					api.setClientOption(pId, "useInventory", true)
					api.setClientOption(pId, "useFullInventory", false)
				}
				let rem = api.getPlayerIds().filter(pId => pId !== player)
				api.removeEffect(player, "Speed")
				api.broadcastMessage(`The tagger (${api.getEntityName(player)}) won!`, {color: "goldenrod"})
				for (let pId of api.getPlayerIds()) {
					api.setClientOption(pId, "middleTextUpper", "The tagger won!")
				}
				api.giveItem(player, "Gold Coin", 10)
				api.sendMessage(player, "You won!")
				r1timer = 0
			}
		} else if (dmgId !== player && api.getEffects(dmgId).includes("Frozen") && atkId !== player && !api.getEffects(atkId).includes("Frozen") && !api.getEffects(atkId).includes("Invisible")) {
			api.removeEffect(dmgId, "Frozen")
			api.sendMessage(atkId, ["Unfroze ", {str: api.getEntityName(dmgId), style: {color: "lime"}}, "!"])
			api.sendMessage(dmgId, "You have been unfrozen!", {color: "goldenrod"})
			api.broadcastMessage([{str: api.getEntityName(dmgId), style: {color: "cyan"}}, " was unfrozen by ", {str: api.getEntityName(atkId), style: {color: "aqua"}}, "!"])
		}
	}
	return "preventDamage"
}

onRespawnRequest = (pId) => {
	if (!game) {
		api.setClientOption(pId, "middleTextUpper", "")
		api.setPosition(pId, [242, 88, 82])
		api.setClientOption(pId, "middleTextLower", "")
		api.setClientOption(pId, "creative", false)
		api.setWalkThroughType(pId, "Glass", true)
		api.setPosition(pId, [242, 88, 82])
		api.setHealth(pId, 100)
		api.removeEffect(pId, "Invisible")
	} else {
		api.setPosition(pId, [242, 88, 82])
		api.setClientOption(pId, "middleTextLower", "You are spectating")
		api.setClientOption(pId, "creative", true)
		api.setWalkThroughType(pId, "Glass")
		api.setPosition(pId, [242, 88, 82])
		api.setHealth(pId, null)
		api.applyEffect(pId, "Invisible", null, {})
	}
}

onPlayerLeave = (pId, shutDown) => {
	if (game && pId === player) {
		api.broadcastMessage("The tagger has left the game", {color: "goldenrod"})
		game = false
		gameTimer = gameLength * 60 * 20 + 1
		api.broadcastMessage("Map changed to Abandoned City", {color: "#CEF3FF"})
		for (let pId of api.getPlayerIds()) {
			api.setClientOption(pId, "RightInfoText", ["Game starting in ", {str: `${waitSeconds}`, style: {color: "lime"}}])
			api.removeEffect(pId, "Frozen")
			api.setTargetedPlayerSettingForEveryone(pId, "nameTagInfo", {backgroundColor: ""})
			api.setHealth(pId, 0)
			api.setHealth(pId, 100)
			api.removeEffect(pId, "Rested Speed")
			api.removeEffect(pId, "Speed")
			api.setTargetedPlayerSettingForEveryone(pId, "hasPriorityNametag", false, false)
			api.setClientOption(pId, "useInventory", true)
			api.setClientOption(pId, "useFullInventory", false)
		}
		api.broadcastMessage("The runners won!", {color: "goldenrod"})
		for (let pId of api.getPlayerIds()) {
			api.setClientOption(pId, "middleTextUpper", "The runners won!")
		}
		for (let pId of api.getPlayerIds()) {
			api.giveItem(pId, "Gold Coin", 10)
			api.sendMessage(pId, "You won!")
		}
		r1timer = 0
	}
}

onPlayerDropItem = (pId, x, y, z, name, amt, idx) => {
	return "preventDrop"
}

onPlayerMoveInvenItem = (pId, idx, sIdx, eIdx, amt) => {
	return "preventChange"
}

onPlayerAltAction = (pId, x, y, z, block, eId) => {
	if (x === 204 && y === 75 && z === 78) {
		let c = api.getInventoryItemAmount(pId, "Gold Coin")
		if (c >= 300) {
			api.removeItemName(pId, "Gold Coin", 300)
			api.giveItem(pId, "Melon Slice")
		} else {
			api.sendMessage(pId, "You need 300 coins to buy Melon Slice", {color: "#CEF3FF"})
		}
	}
	if (x === 205 && y === 105 && z === 60) {
		let c = api.getInventoryItemAmount(pId, "Gold Coin")
		if (c >= 100) {
			api.removeItemName(pId, "Gold Coin", 100)
			api.giveItem(pId, "Banana")
		} else {
			api.sendMessage(pId, "You need 100 coins to buy Banana", {color: "#CEF3FF"})
		}
	}
	if (x === 218 && y === 75 && z === 113) {
		let c = api.getInventoryItemAmount(pId, "Gold Coin")
		if (c >= 200) {
			api.removeItemName(pId, "Gold Coin", 200)
			api.giveItem(pId, "Cracked Coconut")
		} else {
			api.sendMessage(pId, "You need 200 coins to buy Cracked Coconut", {color: "#CEF3FF"})
		}
	}
	if (x === 280 && y === 75 && z === 101) {
		let c = api.getInventoryItemAmount(pId, "Gold Coin")
		if (c >= 50) {
			api.removeItemName(pId, "Gold Coin", 50)
			api.giveItem(pId, "Watermelon Slice")
		} else {
			api.sendMessage(pId, "You need 50 coins to buy Watermelon Slice", {color: "#CEF3FF"})
		}
	}
}

onBlockStand = (pId, x, y, z, block) => {
	if (block === "Block of Moonstone") {
		api.setVelocity(pId, 0, 12, 0)
	}
}
```
