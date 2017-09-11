---
title: Wechaty API 
date: 2017-07-25 14:53:54
tags: wechaty
---

## Events:
* scan: Emit when the bot needs to show you a QR Code for scanning
* login: Emit when bot login is fully successful.
* logout: Emit when bot detects log out.
* message: Emit when there's a new message.
* error: Emit when an error occurs.
* friend: Emit when a new friend request is received, or friendship is confirmed.
* room-join: Emit when someone joins the room
* room-leave: Emit when someone leaves the room
* room-topic: Emit when someone changes the room's topic

## Main Classes
* Wechaty
* Message
* Contact
* Room
* FriendRequest
* MediaMessage

## Classes Details

### 1.Wechaty Class
Main bot class.

```ts
import { Wechaty } from 'wechaty'
```

#### 1.1 Wechaty.instance(profile:string): Wechaty
Create a bot instance

```typescript
const bot = Wechaty.instance({
  profile: 'my-bot'
})
```
#### 1.2  Wechaty.init(): Wechaty
Initialize the bot, return Promise.

```typescript
wechaty.init()
.then(() => {
  // do other stuff with bot here
}
```

#### 1.3 Wechaty.say(content: string)

`Wechaty` is `Sayable`, this method will send message to `filehelper`, just for logging/reporting usage for your convenience


```typescript
wechaty.say('hello')
```

### 2 Message Class

All wechat messages will be encapsulated as a Message.

```ts
import { Message } from 'wechaty'
```

`Message` is `Sayable`

### Message.from(contact?: Contact|string): Contact

Get the sender from a message, or set it.

#### 1. Message.from(): Contact

Get the sender from a message.

#### 2. Message.from(contact: Contact): void

Set a sender to the message

#### 3. Message.from(contactId: string): void

Set a sender to the message by contact id

### Message.to(contact?: Contact|string): Contact|void

Get the receiver from a message, or set it. 

Only deal with Contact, if you need Room, try Message.room()

#### 1. Message.to(): Contact

Get the destination of the message

Message.to() will return null if a message is in a room, use Message.room() to get the room.

#### 2. Message.to(contact: Contact): void

Set the destination as Contact for the message

#### 3. Message.to(contact: string): void

Set the destination as Contact by 'weixin', for the message

### Message.content(content?: string): string

Get the content from a message, or set it.

#### 1. Message.content(): string

Get the content of the message

#### 2. Message.content(content: string): string

Set the content for the message

### Message.room(room?: Room|string): Room|void

Get the room from a message, or set it.

#### 1. Message.room(): Room | null

Get the room from the message. 

If the message is not in a room, then will return `null`

#### 2. Message.room(room: Room): void

Set the room for a message

#### 3. Message.room(roomId: string): void

Set the room by id for a message

### Message.type(): MsgType

Get the type from the message.

Some known value of the type list here is:
* TEXT               1  
* IMAGE              3     
* VOICE              34    
* VERIFYMSG          37
* POSSIBLEFRIEND_MSG 40
* SHARECARD          42
* VIDEO              43
* EMOTICON           47
* LOCATION           48
* APP                49
* VOIPMSG            50
* STATUSNOTIFY       51
* VOIPNOTIFY         52
* VOIPINVITE         53
* MICROVIDEO         62    
* APP                49   
* SYSNOTICE          9999 
* SYS                10000 
* RECALLED           10002

### Message.typeApp(): AppMsgType

Get the app type from message, if not apptype, return 0

Some known value of the type list here is:
* TEXT                      1
* IMG                       2
* AUDIO                     3
* VIDEO                     4
* URL                       5
* ATTACH                    6
* OPEN                      7
* EMOJI                     8
* VOICE_REMIND              9
* SCAN_GOOD                 10
* GOOD                      13
* EMOTION                   15
* CARD_TICKET               16
* REALTIME_SHARE_LOCATION   17
* TRANSFERS                 2e3
* RED_ENVELOPES             2001
* READER_TYPE               100001

### Message.say(content: string): Promise<void>

Reply a message to the sender.

### Message.mentioned(): Contact[]

Return a contactlist which this message is mentioned for?

If the message is "@Botself bla...", then the mention() will return a contactlist contains just bot self contact.

If the message is "@other_user bar...", then the mention() will return a contact for the "other_user".

If no one was mentioned we return []. (contact.mention().length)

About `@` blank in Wechat: It use special char with unicode code `8197` to indetify `real@`

### Message.self(message: Message): boolean

Check if a message is sent by self.

Return `true` for send from self, `false` for send from others.

```typescript
if (message.self()) {
  console.log('this message is sent by myself!')
}
```

### Message.id: string

Get the id from a message

### Message.filename():string

Get the filename from a media message, if not media message, throw Error
 
## Contact Class

```ts
import { Contact } from 'wechaty'
```

`Contact` is `Sayable`

### Contact.id: string

Uniq id

### Contact.name(): string | '' 

Get the name from a contact

### Contact.city(): string | undefined

Get the region 'city' from a contact


### Contact.province(): string | undefined

Get the region 'province' from a contact

### Contact.gender(): Gender | undefine

Get the gender from a contact: 

* Unknown = 0,
* Male    = 1,
* Female  = 2,

### Contact.avatar():

Save avatar to file, simple code as follows: (save contact avator to file `${contact.name()}.jpg`)

``` typescript
// contact: Contact
const avatarFileName = `${contact.name()}.jpg`
const avatarReadStream = await contact.avatar()
const avatarWriteStream = createWriteStream(avatarFileName)
avatarReadStream.pipe(avatarWriteStream)
```

### Contact.alias(): string | null

Get the alias name from a contact

### Contact.alias(alias: string): Promise<boolean>

Set alias name to a contact

Return a Promise<boolean>, true for modified successful, false for failure.

```typescript
const ret = await contact.alias("newAlias")
  if (ret) { 
    console.log('set alias successfulyy!')
  } else {
    console.error('failed to set alias') 
  }
```
use `Contact.alias(null)` to clear alias

### Contact.weixin(): string | ''

Get the weixin number from a contact, 

Sometimes cannot get weixin number due to weixin security mechanism, not recommend.

### Contact.star(): boolean

Check it the contact is star contact.

True for star friend, False for no star friend

### Contact.refresh(): Promise<this>

Force reload data for Contact

### Contact.self(): boolean

Check if contact is self

True for contact is self, False for contact is others

### Contact.stranger(): boolean

Check if contact is strange

True for not friend of the bot, False for friend of the bot

### Contact.say(content: string): Promise<void>

Say `content` to Contact

### Contact Query Type

```typescript
type Query = {
  name?: string | RegExp
  alias?: string | RegExp
}
Contact.find(query : Query) : Contact | null
Contact.findAll(query : Query) : Contact[]
```

### static Contact.find(query: Query): Promise

Find contact by name or alias, if the result more than one, return the first one.

```typescript
const contactFindByName = await Contact.find({ name:"ContactName"} ) 
const contactFindByAlias = await Contact.find({ alias:"ContactAlias"} ) 
```

### static Contact.findAll(query: Query): Promise

Find contact by alias or name, return all the match contact   

If use `Contact.findAll()` get the contact list of the bot.

## Class Room

```ts
import { Room } from 'wechaty'
```

`Room` is `Sayable`

Doc is cheap, show you code: [Example/Room-Bot](https://github.com/wechaty/wechaty/blob/master/example/room-bot.ts)

### Room.say(content: string, replyTo: Contact|Contact[]): Promise<void>

Say `content` inside Room.

If you set `replyTo`, then `say()` will mention them as well.
> "@replyTo content"

### Room.refresh(): Promise<Room>

Force reload data for Room

### Room Events

`this` is `Sayable` for all listeners.

Which means there will be a `this.say()` the method inside listener call, you can use it sending a message to `filehelper`, just for logging/reporting usage for your convenience.

#### Event: `join`

```typescript
Room.on('join', (this: Room, inviteeList: Contact[], inviter: Contact) => void)
```

Event `join`: Room New Member

```typescript
room.on('join', function(inviteeList, inviter) {
  console.log(`the room ${room.topic()}, got new members invited by ${inviter.name()}`)
})
```

#### Event: `leave`

```typescript
Room.on('leave', (this: Room, leaverList: Contact[]) => void)
```

#### Event: `topic`

```typescript
Room.on('topic', (this: Room, topic: string, oldTopic: string, changer: Contact) => void)
```

### Room Query Type

```typescript
type Query = { topic: string|Regex }
Room.find(query : Query) : Room | null
Room.findAll(query : Query) : Room[]
```

### static Room.find(query: Query): Promise<Room>

Find room by topic, if the result more than one, return the first one.

```typescript
Room.find({ topic:"Room Topic"} ) 
  .then(dingRoom =>{
  //Room Operation
  })
```

### static Room.findAll(query: Query): Promise<Room[]>

Find room by topic, return all the match room

### static Room.create(contactList: Contact[], topic?: string): Promise<void>

Create a new room.

### Room.add(contact: Contact): Promise<void>

Add contact in a room

```typescript
const friend = message.get('from')
const room = Room.find({ name: 'Group Name' })
if (room) {
  room.add(friend)
}
```

### Room.del(contact: Contact): void

Delete a contact from the room

### Room.topic(): string

Get topic from the room

### Room.topic(newTopic: string): void

Set topic for the room 

### Room.alias (contact: Contact): string

Get the contact's alias in the room, if the contact doesn't set its roomAlias in the room, it return name.

### Room.has(contact Contact): boolean

Check if the room has member `contact`. 

Return `true` if has contact, else return `false`.

### Room.owner(): Contact|null

Get room's owner from the room.

Not recommend, because cannot always get the owner

### Room.member(name: string): Contact|null

Find the contact by name in the room, equals to `Room.member({name:name}) `

#### notice: 
there are three kinds of names in wechat:
* **Definition**:  
	* **name:** the name-string set by user-self, should be called **name**
	* **room alias:** the name-string set by user-self in a room, should be called **room alias**.  **room alias** only belongs to the room.
	* **contact alias:** the name-string set by bot for others, should be called **contact alias**

* **Display order in wechat room**:
	* **@ Event**   
When someone @ a contact in  a room, wechat recognise the name order as follows:   
`room alias > name`

	* **system message**   
When room event happens(join, leave, changetopic), system message recognise the name order as follows:   
`contact alias > name`

	* **on-screen Names**   
The contact name showed to the wechat user in the group   
`contact alias > room alias > nickName`

* **`Room.member()` query key**:
	* self-set: {name: string}
	* other-set: {alias: string}

### Room.member({alias: string}): Contact|null

Find the contact by alias in the room

### Room.member({name: string}): Contact|null

Find the contact by name in room.

### Room.memberList(): Contact[]

Get all room member from the room

## Class FriendRequest

Send, receive friend request, and friend confirmation events.

```ts
import { FriendRequest } from 'wechaty'
```

When someone sends you a friend request, there will be a Wechaty `friend` event fired.

### FriendRequest.hello: string

Verify message

### FriendRequest.accept(): Promise<boolean>

Accept a friend request

Return a Promise, true for accept successful, false for failure.

### FriendRequest.send(contact: Contact, hello: string): Promise<boolean>

Send a new friend request

Return a Promise, true for accept successful, false for failure.

```typescript
const from = message.from()
const request = new FriendRequest()
request.send(from, 'hello~')
```
## Class MediaMessage

Create a media message object.

```ts
import { MediaMessage } from 'wechaty'
```
### new MediaMessage(path: string)
```ts
message.say(new MediaMessage('images.jpg'))
```

