
# setup dvc
```
git init
dvc init
git status
git add .dvc
git commit -m "DVC init"
dvc status
```

# get data
```
dvc get https://github.com/iterative/dataset-registry \ 
          get-started/data.xml -o data/data.xml
```

# add a file
```
dvc add data/data.xml -v
git add data/.gitignore data/data.xml.dvc
git commit -m "Add raw data"
```

# add a directory
## download data
```
git checkout -b cats-dogs-v1

dvc get --rev cats-dogs-v1 \
              https://github.com/iterative/dataset-registry \
              use-cases/cats-dogs -o datadir
```
## add and track dir
```
dvc add datadir

git status

git add .gitignore datadir.dvc,
git commit -m Add datadir,
git tag -a cats-dogs-v1 -m Create data version v1
```



# switching versions

## create a branch
```
dvc status
git checkout -b cats-dogs-v2
dvc get --rev cats-dogs-v2 ,
```


## add data to branch
```
dvc status 
dvc add datadir

git status
git add datadir.dvc,
git commit -m Change data,
git tag -a cats-dogs-v2 -m Create data version v2
```

## switch branch
```
git checkout tutorial,
dvc checkout
```
as we can see datadir has disappeared


## switch back
git checkout cats-dogs-v1

## Still - No `datadir` directory there Why? ,
```
dvc status
dvc checkout
```
# setup remote storage (local in this case)

## add remote
```
dvc status
mkdir -p ~/.tmp/dvc,
dvc remote add -d local /tmp/dvc
```

## check setup

```
dvc remote list
```

```
git status -s
dvc push -v
rm -rf .dvc/cache,
rm -rf datadir
```
## pull from remote storage

```
dvc pull -v
```