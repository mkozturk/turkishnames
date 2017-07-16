# turkishnames

I have tallied and analyzed names and birthdates of about 50 million Turkish citizens. I present the results and aggregated data in this repository. The raw data is not made available in order to prevent possible violations of privacy.

## Overview
The data contains records of 49,611,709 individuals, 24,534,483 men and 25,077,226 women, born between 1888 and 1991.

All strings are in capital letters and non-ASCII Turkish characters are converted to ASCII (Ü->U, Ö->O, İ->I, Ş->S, Ğ->G, Ç->C).

The raw data is given in text form. I have used simple Python scripts to extract relevant data and to tally counts. I have also used command-line tools such as awk, grep, wc for quick filtering and counting.

## Most common male and female first names
In parsing the names, I have counted first and middle names separately. For example, a man named Mehmet Ali is counted under MEHMET as well as ALI.

The 20 most common male names

First name | Count
-----------|------
MEHMET | 1681870
ALI | 1026732
MUSTAFA | 991402
AHMET | 832581
HUSEYIN | 599081
HASAN | 575189
IBRAHIM | 500358
MURAT | 440120
ISMAIL | 417622
OSMAN | 340200
HALIL | 288916
RAMAZAN | 286392
OMER | 279963
YUSUF | 252189
SULEYMAN | 214209
ABDULLAH | 202199
KEMAL | 181997
FATIH | 180101
MAHMUT | 168177
RECEP | 164173

The 20 most common female names

First name | Count
-----------|------
FATMA | 1228293
AYSE | 969973
EMINE | 787293
HATICE | 687368
ZEYNEP | 333301
MERYEM | 218986
ELIF | 216261
SULTAN | 179158
HULYA | 171124
SEVIM | 168463
OZLEM | 165682
SERIFE | 164457
FADIME | 160452
HANIFE | 155109
AYSEL | 154638
DILEK | 149858
ZEHRA | 149354
YASEMIN | 148887
HACER | 147168
HAVVA | 145851

One can also wonder about the _least_ common names. However, the distribution of names is long-tailed, meaning there are thousands of names, each carried by only a few people. The database contains 164,820 distinct first names; however, many of them are misspellings or variants of more common names. There are only 25,940 first names that are carried by 10 or more people.

number of people carrying the name | number of distinct names
----------- | -----------
\>= 1 | 164,820
\>= 10 | 25,940
\>= 100 | 7616
\>= 1,000 | 2319
\>= 10,000 | 805
\>= 100,000 | 70
\>= 1,000,000 | 3

There are more than a hundred thousand people with a unique first name, so the question of the least common name does not apply.

Female first names have more variation than male first names. Of all first names used by at least 100 people, 4899 are female and 3189 are male.

# Unisex first names

There are many Turkish names that are used by either gender, such as Deniz, Kamuran, Tuna, etc. However, when I tried to tally the names that occur both in male and female list, I was surprised to see that exclusively male and female names also appeared on the list. For example, there are 69 Mehmets listed as female (out of 1.7 million) and 48 Fatmas listed as male (out of 1.2 million). These are obviously clerical mistakes. In order to eliminate them, I discounted the names where one gender's count is less than 1/20th of the other. Here are the most common 20 unisex names:

Name | Males | Females | Total count
---|---| --- | ---
YASAR | 161295 | 20662 | 181957
AYHAN | 99641 | 12362 | 112003
YUKSEL | 56679 | 44158 | 100837
ISMET | 79623 | 11568 | 91191
DURSUN | 74131 | 15564 | 89695
MUZAFFER | 75073 | 7317 | 82390
UMIT | 72587 | 6411 | 78998
DENIZ | 32900 | 43779 | 76679
HIKMET | 53208 | 20450 | 73658
OZGUR | 61928 | 5121 | 67049
ILHAN | 60225 | 3717 | 63942
FIKRET | 49488 | 3325 | 52813
OZCAN | 47837 | 3733 | 51570
NIMET | 4029 | 46739 | 50768
SATI | 3767 | 44062 | 47829
CIHAN | 40260 | 6288 | 46548
SUAT | 41030 | 2604 | 43634
SERVET | 30728 | 10998 | 41726
SERIF | 35247 | 5892 | 41139
NUR | 3286 | 35213 | 38499

The names above are sorted according to their overall count. However, many of them are biased toward being male names. Alternatively, one can sort them according to some "equality score", which I define as 1 - |males - females|/total. So if a name is carried by an equal number of people in each gender its score is 1. If there is a strong bias for one gender, its score is close to 0.

Here are the first 20 unisex names sorted according to the equality score. We count only names that occur more than 10,000 people.

Name | Male | Female | Total | Score
-----|----|----|----|----
EMIR | 8662 | 8309 | 16971 | 0.9792
MUHTEREM | 5027 | 5568 | 10595 | 0.948938
KAMURAN | 7255 | 5739 | 12994 | 0.883331
YUKSEL | 56679 | 44158 | 100837 | 0.875829
DENIZ | 32900 | 43779 | 76679 | 0.858123
OMUR | 8198 | 6159 | 14357 | 0.857979
SIRIN | 11878 | 15828 | 27706 | 0.857432
FERHAN | 4128 | 5934 | 10062 | 0.820513
ERGUL | 4737 | 7036 | 11773 | 0.804723
SENEL | 6043 | 9012 | 15055 | 0.80279
HIDAYET | 17361 | 10769 | 28130 | 0.765659
GUNGOR | 10690 | 6559 | 17249 | 0.760508
OLCAY | 11721 | 6038 | 17759 | 0.679993
DURDU | 8449 | 16604 | 25053 | 0.67449
SAFAK | 7392 | 3751 | 11143 | 0.673248
ILKAY | 6526 | 13337 | 19863 | 0.657101
SEZER | 8624 | 4000 | 12624 | 0.633714
GUNAY | 8221 | 18257 | 26478 | 0.620968
HIKMET | 53208 | 20450 | 73658 | 0.555269

## Most common last names
Just as in first names, I have counted double last names separately. The most common 20 last names are:

Last Name | Count
------|------
YILMAZ | 712772
KAYA | 490839
DEMIR | 463847
SAHIN | 406697
CELIK | 400976
YILDIZ | 391630
YILDIRIM | 387084
OZTURK | 361303
AYDIN | 358847
OZDEMIR | 331830
ARSLAN | 295082
DOGAN | 281281
KILIC | 247886
CETIN | 208683
ASLAN | 208155
KARA | 170395
KOC | 167971
KURT | 161857
OZKAN | 157206
ACAR | 149566

There is a total of 189,094 unique last names, including misspellings and inconsistently entered double last names (e.g., using hyphens or parentheses). Here is a breakdown of unique last names and number of people having it.

number of people | number of distinct last names
----------- | -----------
\>= 1 | 189,094
\>= 10 | 114,918
\>= 100 | 28,606
\>= 1,000 | 4,941
\>= 10,000 | 721
\>= 100,000 | 48
\>= 1,000,000 | 0

An interesting observation is that there are more last names than first names, even accounting for misspellings. For example, there are about 115,000 unique last names, carried by 10 or more people, compared to 26,000 such first names.

## People with the same first and last names
As an interesting aside, I counted people who had the same first and last names. Turns out there are several thousand such people, and more than 1500 such combinations. Here is the top 22:

First name | Last name | Count
-----|-----|-----
YILMAZ | YILMAZ | 499
YILDIZ | YILDIZ | 479
AYDIN | AYDIN | 303
SAHIN | SAHIN | 299
DOGAN | DOGAN | 185
BAYRAM | BAYRAM | 172
GULER | GULER | 171
YASAR | YASAR | 161
ARSLAN | ARSLAN | 153
DURSUN | DURSUN | 106
DURMUS | DURMUS | 98
YUKSEL | YUKSEL | 94
SEVIM | SEVIM | 90
KAYA | KAYA | 87
CETIN | CETIN | 78
ASLAN | ASLAN | 73
TURAN | TURAN | 70
YALCIN | YALCIN | 69
OZCAN | OZCAN | 68
BEKTAS | BEKTAS | 59
OZKAN | OZKAN | 59
DURAN | DURAN | 58

This time I went up to 22, because as a kid of 80s I just had to show the "Duran Duran" on the list.
