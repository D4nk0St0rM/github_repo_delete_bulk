### How to manage / delete in bulk github repos

- Use chrome
  - install [OneTab](https://chrome.google.com/webstore/detail/onetab/chphlpgkkbolifaimnlloiipkdnihall?hl=en)
- Create key for repo delete
  - [Github Token Create](https://github.com/settings/tokens/new)  
- Open all repos you wish to delete in seperate chrom tabs
- Use OneTab to copy paste all URLs and titles of open tabs
  - vim repo.list / paste URLs & titles

```
cat repo.list | awk -F " | " '{print $1}' | awk -F "/" '{print $4,$5}' | sed 's/ /\//' | sed '1d;$d' > del.list

while read repo;
do 
  curl -XDELETE -H 'Authorization: token xxx' "https://api.github.com/repos/$repo ";
done 
  < del.list

```


