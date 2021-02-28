# NOctuInjector Documentation

**NOctuInjector c'est quoi ?**
*Simplement, c'est un langage de script qui peut être utilisé pour moddé n'importe quel serveur Minecraft sous mcp.*

Tout d'abord, le langage utiliser est le javascript MAIS ne vous inquitez pas ^^

Vous n'avez besoins d'aucune compétence particulière en codage tellement c'est simple :D

Voici un exemple de script basique:

```javascript
function onLoad(){
    mc.getPlayer().addChatMessage('Hello World!');
}
```

Ce que fait ce script c'est qu'il attend le onLoad() et ajoute un message côté client :)

Si vous êtes convaincu par cet exemple je vous invite à poursuivre...

## ApiMinecraft

**ApiMinecraft** est une class accessible en utilisant l'instance: 

```javascript
mc
```

**ApiMinecraft** vous permet d'obtenir des éléments du jeu, voici la liste de ceux ci:

**Fonctions:**

```javascript
getPlayer() //retourne un objet ApiEntityClientPlayerMP, vous donne le joueur local

getPlayerController() //retourne un objet ApiPlayerControllerMP, vous donne le playercontroller

getFontRenderer() //retourne un objet ApiFontRenderer, vous donne le fontrenderer de minecraft

getWorld() //retourne un object ApiWorld, vous donne le monde dans lequel vous êtes actuellement

```

## Events

**Les Events** sont là pour vous fournir des supports d'injection.
Par exemple quand un tick s'écoule, ou alors quand un packet s'envoi.

### OnLoad

**OnLoad** est une fonction qui est appelée quand le script est chargé.

Exemple:
```javascript
function onLoad(){
	Console.info('Le script est chargé');
}
```

### OnUpdate

**OnUpdate** est une fonction qui est appelée à peu près à chaque tick du jeu.

Exemple:
```javascript
function onUpdate(){
	Console.info('ticked');
}
```

### OnRender

**OnRender** est une fonction qui est appelée au rendu du jeu.

Elle vous permet de dessiner sur l'écran.

Exemple:
```javascript
function onRender(){
	Drawing.drawFilledRectangle(10, 10, 200, 100, 0xffffffff);
}
```

### OnPacket

**onPacket** est une fonction qui est appelée quand un packet est envoyé/reçu.

Exemple:
```javascript
function onPacket(event){
	event.getC01Packet();
}
```

#### ApiEventPacket

**L'event packet** est l'event qui est appelé quand un packet est envoyé/reçu.

**Fonctions:**

```javascript
isC01PacketMessage() //retourne un boolean, donne si le packet envoyé est bien un packet de C01

getC01Packet() //retourne un ApiC01PacketMessage, donne le packet de C01 envoyé

isC03PlayerPacket() //retourne un boolean, donne si le packet envoyé est bien un packet de C03

isC04PacketPosition() //retourne un boolean, doonne si le packet envoyé est bien un packet de C04

isC05PacketLook() //retourne un boolean, donne si le packet envoyé est bien un packet de C05

isC07PlayerDiggingPacket() //retourne un boolean, donne si le packet envoyé est bien un packet de C07

isS12PacketVelocity() //retourne un boolean, donne si le packet reçu est bien un packet de S12

replacePacketWith(ApiPacket packet) //remplace le packet qui est envoyé/reçu par un autre

isCancelled() //retourne un boolean, donne si l'event est annulé (si il est annulé, le packet de l'event ne sera pas envoyé/reçu)

setCancelled(boolean cancelled) //permet d'annulé l'event (si il est annulé, le packet de l'event ne sera pas envoyé/reçu)
```

## Entities

**Les entitées** sont des objets comme le joueur, les moutons, les zombies ou encore les items drop

### ApiEntity

**ApiEntity** est la base de toutes les entitées de mc, toute les entitées partent de cette class.

**Fonctions:**

```javascript
getPosX() //retourne un double, donne la position X de l'entitée

getPosY() //retourne un double, donne la position Y de l'entitée

getPosZ() //retourne un double, donne la position Z de l'entitée

setPosX(double posX) //défini la position X de l'entitée

setPosY(double posY) //défini la position Y de l'entitée

setPosZ(double posZ) //défini la position Z de l'entitée

getMotionX() //retourne un double, donne le mouvement X de l'entitée

getMotionY() //retourne un double, donne le mouvement Y de l'entitée

getMotionZ() //retourne un double, donne le mouvement Z de l'entitée

setMotionX(double motionX) //défini le mouvement X de l'entitée

setMotionY(double motionY) //défini le mouvement Y de l'entitée

setMotionZ(double motionZ) //défini le mouvement Z de l'entitée

getRotationYaw() //retourne un float, donne la rotation yaw de l'entitée

getRotationPitch() //retourne un float, donne la rotation pitch de l'entitée

getFallDistance() //retourne un float, donne la distance de chute de l'entitée

onGround() //retourne un boolean, donne si le joueur est sur le sol ou pas

setOnGround(boolean onGround) //défini si le joueur est sur le sol ou pas

noClip() //retourne un boolean, donne si le joueur est en phase de noclip ou pas

setNoClip() //défini si le joueur est en phase de noclip ou pas

getBoundingBox() //retourne un ApiAxisAlignedBoundingBox, donne la boite de collision du joueur

setPosition(double posX, double posY, double posZ) //défini la position du joueur

getDistanceTo(ApiEntity entity) //retourne un double, donne la distance entre cette entitée et une autre

isLocalPlayer() //retourne un boolean, donne si l'entitée est le joueur local

isEntityLivingBase() //retourne un boolean, donne si l'entitée est une entitée de type ApiEntityLivingBase ou pas

getEntityLivingBase() //retourne un ApiEntityLivingBase, donne l'entitée living base correspondant à cette entitée

isEntityPlayer() //retourne un boolean, donne si l'entitée est une entitée de type ApiEntityPlayer ou pas

getEntityPlayer() //retourne un ApiEntityPlayer, donne l'entitée player correspondant à cette entitée
```

### ApiEntityLivingBase

**ApiEntityLivingBase** représente une entitée vivante.

**Fonctions:**

```javascript
getMoveStrafing() //retourne un float, donne la force de déplacement horizontale

getMoveForward() //retourne un float, donne la force de déplacement verticale
```

### ApiEntityPlayer

**ApiEntityPlayer** représente un joueur.

**Fonctions:**

```javascript
getHeldItem() //retourne un ApiItemStack(), donne l'item que le joueur tiens
```

### ApiAbstractClientPlayer

**ApiAbstractClientPlayer** est une class entre **ApiEntityPlayerSP** et **ApiEntiyPlayer** dont je ne connais pas trop l'utilité ^^"

### ApiEntityPlayerSP

**EntityPlayerSP** représente un joueur local.

**Fonctions:**

```javascript
addChatMessage(string message) //ajoute un message au chat local
```

### ApiEntityClientPlayerMP

**ApiEntityClientPlayerMP** est une class qui est utilisée pour le joueur local

**Fonctions:**

```javascript
getSendQueue() //retourne un ApiNetHandlerPlayClient, donne l'object qui permet d'envoyer des packets

swingItem() //joue l'animation de l'item/main que vous avez dans la main

mountEntity(ApiEntity entity) //vous fait monter sur une entitée

sendChatMessage(string message) //envoi un message au serveur en tant que joueur local
```

## Keyboard

**Keyboard** vous permet d'intéragir avec votre clavier.

### Keyboard

**Keyboard** vous permet toujours d'intéragir avec votre claviver.

**Fonctions:**

```javascript
isKeyPressed(int key) //retourne un boolean, donne si la touche est pressé

isKeyDown(int key) //retourne un boolean, donne si la touche est enfoncé
```

### Keys

**Keys** vous permet de vous procurer les int pour les touches.

**Fonctions:**

```javascript
keyA //retourne un int, donne l'int de la touche a
keyB //retourne un int, donne l'int de la touche b
keyC //retourne un int, donne l'int de la touche c
keyD //retourne un int, donne l'int de la touche d
keyE //retourne un int, donne l'int de la touche e
keyF //retourne un int, donne l'int de la touche f
keyG //retourne un int, donne l'int de la touche g
keyH //retourne un int, donne l'int de la touche h
keyI //retourne un int, donne l'int de la touche i
keyJ //retourne un int, donne l'int de la touche j
keyK //retourne un int, donne l'int de la touche k
keyL //retourne un int, donne l'int de la touche l
keyM //retourne un int, donne l'int de la touche m
keyN //retourne un int, donne l'int de la touche n
keyO //retourne un int, donne l'int de la touche o
keyP //retourne un int, donne l'int de la touche p
keyQ //retourne un int, donne l'int de la touche q
keyR //retourne un int, donne l'int de la touche r
keyS //retourne un int, donne l'int de la touche s
keyT //retourne un int, donne l'int de la touche t
keyU //retourne un int, donne l'int de la touche u
keyV //retourne un int, donne l'int de la touche v
keyW //retourne un int, donne l'int de la touche w
keyX //retourne un int, donne l'int de la touche x
keyY //retourne un int, donne l'int de la touche y
keyZ //retourne un int, donne l'int de la touche z
```

## Packets

**Un Packet** est un objet envoyé entre vous et le serveur ou inversement.

### ApiC01PacketMessage

**ApiCO1PacketMessage** est le packet envoyé quand vous envoyez un message dans le chat.

**Fonctions:**

```javascript
getPacketMessage() //retourne un string, donne le message contenu dans le packet

(static) newC01Packet(String message) //retourne un ApiC01PacketMessage, vous permet d'avoir une nouvelle instance d'un ApiC01PacketMessage avec les paramètres que vous voulez
```

### ApiC03PacketPlayer

**ApiC03PacketPlayer** est le packet de base du joueur. Il transmet si le joueur est sur le sol ou pas.

**Fonctions:**

```javascript
(static) newC03Packet(boolean onGround) //retourne un ApiC03PacketPlayer, vous permet d'avoir une nouvelle instance d'un ApiC03PacketPlayer avec les paramètres que vous voulez
```

### ApiC04PacketPosition

**ApiC04PacketPosition** est le packet de position du joueur. Il transmet la position et si le joueur est sur le sol ou pas.

**Fonctions:**

```javascript
(static) newC04Packet(double posX, double posY, double posZ, boolean onGround) //retourne un ApiC04PacketPosition, vous permet d'avoir une nouvelle instance d'un ApiC04PacketPosition avec les paramètres que vous voulez
```

### ApiC05PacketLook

**ApiC05PacketLook** est le packet de rotation du joueur. Il transmet le yaw, le pitch et si le joueur est sur le sol ou pas.

**Fonctions:**

```javascript
(static) newC05Packet(float rotationYaw, float rotationPitch, boolean onGround) //retourne un ApiC05PacketLook, vous permet d'avoir une nouvelle instance d'un ApiC05PacketLook avec les paramètres que vous voulez
```

### ApiC07PacketPlayerDigging

**ApiC07PacketPlayerDigging** est le packet de minage. Il est appelé quand le joueur effectu une action de cassage sur un block.

Il transmet le mode de cassage, la position du block et le côté cassé.

**Fonctions:**

```javascript
(static) newC07Packet(int mode, int blockX, int blockY, int blockZ, int face) //retourne un ApiC07PacketPlayerDigging, vous permet d'avoir une nouvelle instance d'un ApiC07PacketPlayerDigging avec les paramètres que vous voulez
```

## Util

**Util** regroupe tout ce qui est dans le package util de minecraft.

### ApiAxisAlignedBoundingBox

**ApiAxisAlignedBoundingBox** est la bounding box d'un object dans le monde.

**Fonctions:**

```javascript
getMinX() //retourne un double, donne la position minX de la bounding box
getMinY() //retourne un double, donne la position minY de la bounding box
getMinZ() //retourne un double, donne la position minZ de la bounding box
getMaxX() //retourne un double, donne la position maxX de la bounding box
getMaxY() //retourne un double, donne la position maxY de la bounding box
getMaxZ() //retourne un double, donne la position maxZ de la bounding box

setMinX(double minX) //défini la position minX de la bounding box
setMinY(double minY) //défini la position minY de la bounding box
setMinZ(double minZ) //défini la position minZ de la bounding box
setMaxX(double maxX) //défini la position maxX de la bounding box
setMaxY(double maxY) //défini la position maxY de la bounding box
setMaxZ(double maxZ) //défini la position maxZ de la bounding box
```

### ApiScaledResolution

**ApiScaledResolution** est une class qui vous permet d'avoir la longueur et la hauteur de l'écran.

**Fonctions:**

```javascript
getScaledWidth() //retourne un int, donne la longueur de l'écran

getScaledHeight() //retourne un int, donne la hauteur de l'écran
```

## Render

Tous ce qui est dans **Render** est ce qui va servir à dessiner sur l'écran avec le ```onRender()```

### ApiFontRenderer

**ApiFontRenderer** sert à afficher et manipuler des strings sur l'écran

**Fonctions:**

```javascript
FONT_HEIGHT //retourne un int, donne la taille Y de la police de minecraft

drawString(string text, int posX, int posY, int coleur, boolean shadow) //retourne un int, dessine un string sur l'écran

getStringWidth(string text) //retourne un int, donne la taille d'un string sur l'écran 
```

## World

**World** regroupe tous ce qui est en rapport avec un monde Minecraft.

### ApiWorld

**ApiWorld** représente un monde Minecraft.

**Fonctions:**

```javascript
getLoadedEntityList() //donne la liste des entitées chargées (à utiliser comme ceci: Java.from(world.getLoadedEntityList()))
```

## Items

**Items** regroupe tous ce qui est en rapport avec les items.

### ApiItemStack

**ApiItemStack** représente un item normal.

**Fonctions:**

```javascript
setDisplayName(string name) //retourne un ApiItemStack, modifie le nom de l'item

useItemRightClick(ApiWorld world, ApiEntityPlayer player) //retourne un ApiItemStack, utilise l'action associé au clique droit de l'item
```

## Network

**Network** regroupe tous ce qui est en rapport avec le réseau.

### ApiPlayerControllerMP

**ApiPlayerControllerMP** permet de controller les actions du joueur local.

**Fonctions:**

```javascript
getCurrentBlocKDamageMP() //retourne un float, donne le nombre de dégats infligés à un block

setCurrentBlocKDamageMP(float damage) //défini les dégats infligés au block que vous êtes entrain de casser

attackEntity(ApiEntity entity) //attaque une entitée

sendUseItem(ApiEntityPlayer player, ApiWorld world, ApiItemStack item) //utilise un item

clickBlockCreative(int i, int ii, int iii, int iii) //aucune idée

windowClick(int windowId, int slotId, int i, int clickMod, ApiEntityPlayer player) //clique sur un slot d'une fenêtre
```

### ApiNetHandlerPlayClient

**ApiNetHandlerPlayClient** vous permez d'envoyer des packets.

**Fonctions:**

```javascript
sendC01PacketMessage(string message) //envoi un packet de C01

sendC03PacketPlayer(boolean onGround) //envoi un packet de C03

sendC04PacketPosition(double posX, double posMinY, double posY, double posZ, boolean onGround) //envoi un packet de C04

sendC05PacketLook(float rotationYaw, float rotationPitch, boolean onGround) //envoi un packet de C05

sendC07PacketPlayerDigging(int mode, int blockX, int blockY, int blockZ, int face) //envoi un packet de C07
```

## Autres

**Autres** regroupe surtout des utilitaires fait pas moi.

### Console

**Console** vous permet d'écrire des messages dans la console.

**Fonctions:**

```javascript
info(string message) //envoi une info dans la console

warning(string message) //envoi un warning dans la console

error(string message) //envoi une error dans la console
```

### ApiMovementUtils

**ApiMovementUtils** regroupe des fonctions pour mieux maitriser les mouvements des entitées.

**Fonctions:**

```javascript
getDirection(ApiEntityLivingBase entityLiving) //retourne un float, donne la direction d'une entitée

setSpeed(ApiEntityLivingBase entityLiving, double speed) //change la vitesse d'une entitée

getSpeed(ApiEntityLivingBase entityLiving) //retourne un double, donne la vitesse d'une entitée

isMoving(ApiEntityLivingBase entityLiving) //retourne un boolean, donne si l'entitée est en mouvement

vClip(ApiEntityLivingBase entityLiving, double height) //change la position Y d'une entitée
```

### Drawing

**Drawing** regroupe des fonctions pour dessiner sur l'écran.

**Fonctions:**

```javascript
drawFilledRectangle(int x, int y, int width, int height, int color) //dessine un rectange rempli sur l'écran

drawFilledCircle(int x, int y, int radius, int color) //dessine un cercle rempli sur l'écran

drawCircle(int x, int y, double radius, int color) //dessine un cercle sur l'écran

drawGradientRectangle(int x, int y, int width, int height, int color1, int color2) //dessine un rectangle avec dégradé sur l'écran

drawSideGradientRect(float x, float y, float width, float height, int color1, int color2) //dessine un rectangle avec dégradé dans un sens différent que la première fonction
```

### MIsc

**Misc** regroupe le reste.

**Fonctions:**

```javascript
displayCreateWorld() //affiche le gui pour créer un monde solo, ne marche pas toujours
```