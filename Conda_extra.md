## Exporting env as YAML
1. If in the environment
```
conda env export > filename.yml
```
2. If not in env
```
conda env export -n name_of_env > filename.yml
```

## Creating env with exported YAML with a prefix
```
conda env create -p PREFIX --file filename.yml
```

## Adding a prefixed location to search path for envs
```
conda config --append envs_dirs dir_path
conda activate env_name
```

## Example usage
``` 
conda env export -n aero > aero.yml
conda create -p D:\Folder\conda\aero --file aero.yml
conda config --append env_dirs D:\Folder\conda\
```
