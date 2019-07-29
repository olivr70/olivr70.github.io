## le file system

### volumes

#### [`df`](https://linux.die.net/man/1/df) : report file system disk space usage

`df -h -T` - affiche l'espage libre des différents mount points

- `-t <fs>` - seulement les partitions de type **fs**
- `-x <fs>` - exclut les partitions de type **fs**
- `-l`, `--local` - seulement les partitions locales

### links

- `ln target_file link_name` - crée un hardlink vers **target_file**
- `ln -s target_file link_name` - crée un softlink vers **target_file**

### directory structure

![Linux directories](./linux-system-directoies-poster-724x1024.png)

### Articles

- [How to Create Symbolic Links in Linux [Complete Guide]](https://linuxhandbook.com/symbolic-link-linux/)
- [Hard Link in Linux: Everything Important You Need to Know](https://linuxhandbook.com/hard-link/?utm_source=newsletter&utm_medium=email&utm_campaign=linux_directory_structure_free_df_and_sort_commands_example_hard_and_soft_links_and_more&utm_term=2019-07-28)
