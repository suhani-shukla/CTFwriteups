# Big Zip

## Challenge

Unzip this archive and find the flag.

## Hints

1. Can `grep` be instructed to look at every file in a directory and its subdirectories?

## Solution

1. List the archive contents.

   ```bash
   unzip -l big-zip-files.zip
   ```

1. Extract the archive.

   ```bash
   unzip big-zip-files.zip
   ```

1. Search recursively for the flag pattern.

   ```bash
   grep -r "pico" big-zip-files
   ```

1. Read the matching file output and get the flag.

   ```text
   folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt:information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}
   ```

## Flag

```
picoCTF{gr3p_15_m4g1c_ef8790dc}
```
