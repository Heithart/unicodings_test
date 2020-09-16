# Difference between UTF-8 and UTF-16
### And what is Unicode

**UTF-8** and **UTF-16** are both text encodings, developed as a representation of the Unicode standard. 
Text information is stored and transmitted as a sequence of bites and encodings serve to translate it to human languages.

At the dawn of technology when humans faced the need to translate from human language to machine, an encoding table  was presented. It was called **ASCII** and it was just a **8x16 table**. It used only one byte to code the symbol. So, programmers had 128 symbols to work with. This was enough to work with text in English language, but soon it appeared that some Western-European languages need more space to store letters with diacritical signs and special symbols. More than that, there are Asian languages with hieroglyphic writing, which increases the need for space in the table. 

This was the reason for dedication of two bytes per symbol and inventing the **UCS-2** encoding. Differences in computer architecture quickly lead to introducing **UCS-BE** and **UCS-LE** - encodings with different positions of the high bits. 

> BE stands for Big Endian.
> LE - Little Endian.

Such tendency threatened with further encoding table growth and problems with compatibility between machines.
So the Unicode standard was to solve the problem by expanding the table and introducing new algorithms of coding symbols. Unicode is represented by **UTF-8** and **UTF-16** (and others).

**UTF-8** extanded the 128-bit **ASCII** table up to 4 bytes per symbol. In UTF- the number of bytes per symbol is not prescripted and grows as long as the symbol’s position number grows. In *UTF-8 first 128 symbols are similar to ASCII* and are coded with only one byte. Western-European and Cyrillic symbols need two  bytes and hieroglyphic writings - three or more. As bits in a computer are stored in ascending order, UTF-8б still being a table, does not need the concept of **BE/LE** and other tricks like UTF-16.

Initially **UTF-16** reserved two bytes per symbol as **USC-2** did, but soon it became clear that it was bytes are not enough and the third byte was added. This makes sense but also this causes a problem: most computers already work with 2-bytes text representation. That is why in UTF-16, when it is necessary to use 3 bytes, first two bytes compose the surrogate pair with the third one. This solves the issue, but still *UTF-16 needs a BE/LE mark*.

So we can see that to encode any text in most usable languages **UTF-8** is enough as this is a simple and capacious way. Besides, it does not need *encoding type* markings in the beginning of the text. As UTF-8 is still a table, any error in the sequence will not affect the whole text, but will be read just as a wrong symbol which is easy to locate and correct.

On the other hand, most machine communications and data transfer are organised as a two-bytes system, and originated from USC-2. This leads to the fact that **UTF-16** is better for such purposes. This involves *API* too. 

So the conclusion is **UTF-16** is better for inter-machine communication, when **UTF-8** is sufficient for a *plain-text editor*. By the way, *Notepad++* does not support **UTF-16** without corresponding plugins, but uses **USC-2** instead.

***
Source used:  
http://www.unicode.org/faq/utf_bom.html  
https://habr.com/ru/post/377953/  
https://qastack.ru/software/102205/should-utf-16-be-considered-harmful
