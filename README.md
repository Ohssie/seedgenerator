# seedgenerator
This is actually a proof of concept for a seed code generator for a laravel project we worked on. Instead of manually coding seeds to be able to have a hug recordset for test purpose, one should only upload an excel file and then the seed codes are generated. This result into creating a new file called seed.php prepopulated with the seed codes. This code took me 10 minutes which should have taken 3 days if i were to write this code manually.

1. Make sure you set proper permission in your app directory for file creation.
2. Ensure the sample_data.csv is in same directory as your application. (not really compulsory, just incase you are having issues)
3. You can tweak code to reduce the size of file
4. Buy me bear if you find it useful


It was a large file so i used terminal to split it into tiny chunks of files

split -b 100k -d -a 3 seed.php seeds. (NOTE: there is a tradeoff with the split command, i have a very small RAM and so i was willing to go ahead. The tradeoff is there are tendencies for texts to be truncated on individual files. This is not neccessary if you can open the large seed file without having your system hanging)
