emoji4j
=============

# 引入Maven依赖
```
<dependency>
	<groupId>com.kcthota</groupId>
	<artifactId>emoji4j</artifactId>
	<version>5.0</version>
</dependency>
```

# Demo测试

## getEmoji
```
Emoji emoji = EmojiUtils.getEmoji("🐭"); //get emoji by unicode character
EmojiUtils.getEmoji("blue_car").getEmoji(); //returns 🚙
EmojiUtils.getEmoji(":blue_car:").getEmoji(); //also returns 🚙
EmojiUtils.getEmoji("&#x1f42d;").getEmoji(); //returns 🐭
EmojiUtils.getEmoji("&#128045;").getEmoji(); //also returns 🐭
EmojiUtils.getEmoji(":)").getEmoji(); //returns 😃
EmojiUtils.getEmoji("&#55357;&#56833;").getEmoji(); //returns 😁
```

## The Emoji Object
```
Emoji emoji = EmojiUtils.getEmoji("🐭");
emoji.getEmoji(); //returns 🐭
emoji.getDecimalHtml(); //returns &#128045;
emoji.getHexHtml(); //return &#x1f42d;
emoji.getAliases(); //returns a collection of aliases. ["mouse"]
```

## isEmoji
```
EmojiUtils.isEmoji("🐭"); //returns true
EmojiUtils.isEmoji("blue_car"); //returns true
EmojiUtils.isEmoji(":coyote:"); //returns false
EmojiUtils.isEmoji("&#x1f42d;"); //returns true
EmojiUtils.isEmoji("&#128045;"); //returns true
```

## emojify
```
String text = "A :cat:, :dog: and a :mouse: became friends<3. For :dog:'s birthday party, they all had :hamburger:s, :fries:s, :cookie:s and :cake:.";
EmojiUtils.emojify(text); //returns A 🐱, 🐶 and a 🐭 became friends❤️. For 🐶's birthday party, they all had 🍔s, 🍟s, 🍪s and 🍰.
String text = "A &#128049;, &#x1f436; and a :mouse: became friends. For the :dog:'s birthday party, they all had :hamburger:s, :fries:s, :cookie:s and :cake:."
EmojiUtils.emojify(text); //returns A 🐱, 🐶 and a 🐭 became friends. For the 🐶's birthday party, they all had 🍔s, 🍟s, 🍪s and 🍰.
String text=":):-),:-):-]:-xP=*:*<3:P:p,=-)";
EmojiUtils.emojify(text); //returns 😃😃😅😃😶😝😗😗❤️😛😛😅
```

## htmlify
```
String text = "A :cat:, :dog: and a :mouse: became friends. For the :dog:'s birthday party, they all had :hamburger:s, :fries:s, :cookie:s and :cake:.";
EmojiUtils.htmlify(text); //returns A &#128049;, &#128054; and a &#128045; became friends. For the &#128054;'s birthday party, they all had &#127828;s, &#127839;s, &#127850;s and &#127856;.
String text = "A 🐱, 🐶 and a 🐭 became friends. For the 🐶's birthday party, they all had 🍔s, 🍟s, 🍪s and 🍰."
EmojiUtils.htmlify(text); //also returns A &#128049;, &#128054; and a &#128045; became friends. For the &#128054;'s birthday party, they all had &#127828;s, &#127839;s, &#127850;s and &#127856;.
```

## hexHtmlify
```
String text = "A :cat:, :dog: and a :mouse: became friends. For the :dog:'s birthday party, they all had :hamburger:s, :fries:s, :cookie:s and :cake:.";
EmojiUtils.hexHtmlify(text); //returns A &#x1f431;, &#x1f436; and a &#x1f42d; became friends. For the &#x1f436;'s birthday party, they all had &#x1f354;s, &#x1f35f;s, &#x1f36a;s and &#x1f370;.
String text = "A 🐱, 🐶 and a 🐭 became friends. For the 🐶's birthday party, they all had 🍔s, 🍟s, 🍪s and 🍰."
EmojiUtils.hexHtmlify(text); //returns A &#x1f431;, &#x1f436; and a &#x1f42d; became friends. For the &#x1f436;'s birthday party, they all had &#x1f354;s, &#x1f35f;s, &#x1f36a;s and &#x1f370;.
```

## htmlify as Surrogate Entities
```
String text = "😃";
EmojiUtils.htmlify(text, true); //returns &#55357;&#56835;
```

##shortCodify
```
String text = "A 🐱, 🐶 and a 🐭 became friends❤️. For 🐶's birthday party, they all had 🍔s, 🍟s, 🍪s and 🍰.";
EmojiUtils.shortCodify(text); //returns A :cat:, :dog: and a :mouse: became friends:heart:. For :dog:'s birthday party, they all had :hamburger:s, :fries:s, :cookie:s and :cake:.
text = ":):-),:-):-]:-xP=*:*<3:P:p,=-)";
EmojiUtils.shortCodify(text); //returns :smiley::smiley::sweat_smile::smiley::no_mouth::stuck_out_tongue_closed_eyes::kissing::kissing::heart::stuck_out_tongue::stuck_out_tongue::sweat_smile:
```

## RemoveAllEmojis
Removes unicode emoji characters from the passed string
```
String emojiText = "A 🐱, 🐱 and a 🐭 became friends❤️. For 🐶's birthday party, they all had 🍔s, 🍟s, 🍪s and 🍰.";
EmojiUtils.removeAllEmojis(emojiText);//"A ,  and a  became friends. For 's birthday party, they all had s, s, s and .
```

## countEmojis
```
String text = "A &#128049;, &#x1f436;,&nbsp;:coyote: and a :mouse: became friends. For :dog:'s birthday party, they all had 🍔s, :fries:s, :cookie:s and :cake:.";
EmojiUtils.countEmojis(text); //returns 8
```
