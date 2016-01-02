# Unix Commands to Process Text files
### Replace the complement of all non-alphabetic character with a new line, one word per line

`$ tr -sc 'A-Za-z' '\n' < shakes.txt | less`

### Sort
`$ tr -sc 'A-Za-z' '\n' < shakes.txt | sort | less`

### Sort with uniqueness. `uniq` will give a count on the usage of a word
`$ tr -sc 'A-za-z' '\n' < shakes.txt | sort | uniq -c | less`

### Let''s take a look now at the list sorted based on frequency rather than alphabetically
`$ tr -sc 'A-Za-z' '\n' < shakes.txt | sort.txt | sort | uniq -c | sort -n -r | less`

### But, now we see that 'The' and 'the' are not properly mapped. Let''s fix that.
`$ tr 'A-Z' 'a-z' < shakes.txt | tr -sc 'A-Za-z' '\n' | sort | uniq -c | sort -n -r | less`

### ... But now we have another problem. We have not dealt with words that use apostrophes. This means that in text such as that from Shakespeare words like "Ophelia's" and "dimm'd" will be tokenized to "Ophelia s" and "dimm d".

Hence we have decide/define how we are going to tokenize words such as "Hewlett-Packard" and words such as "Ophelia's". The problem becomes harder when use look into tokenization in French (l''ensemble) , German (german noun compounds not segmented, Lebensversicherungsgesellschaftsangestllter - life insurance company employee). Also in languages such as Chinese and Janapense were there are no spaces between words.

Furthermore it becomes more complicated in Japanese, as we have to deal with multiple alphabets intermingled: Katakana, Hiragana, Kanji, Romaji
