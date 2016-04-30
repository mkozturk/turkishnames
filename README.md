# turkishnames

I have tallied and analyzed names and birthdates of about 50 million Turkish citizens. I present the results and aggregated data in this repository. The raw data is not made available in order to prevent possible violations of privacy.

##Overview
The data contains records of 49,611,709 individuals, 24,534,483 men and 25,077,226 women, born between 1888 and 1991.

All strings are in capital letters and non-ASCII Turkish characters are converted to ASCII (Ü->U, Ö->O, İ->I, Ş->S, Ğ->G, Ç->C).

The raw data is given in text form. I have used simple Python scripts to extract relevant data and to tally counts. I have also used command-line tools such as awk, grep, wc for quick filtering and counting.

##Most common male and female first names
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
>= 1 | 164,820
>= 10 | 25,940
>= 100 | 7616
>= 1,000 | 2319
>= 10,000 | 805
>= 100,000 | 70
>= 1,000,000 | 3

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

Here are the first 20 unisex names sorted according to the equality score. We 
