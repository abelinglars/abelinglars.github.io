---
layout: post
title: "Trailing slashes in the Docker COPY command"
date: 2025-10-25
toc: true
---

**TLDR**: Trailing slashes in the source are irrelevant, in the destination you need them if you want to ensure the path is treated as a directory.

---

Because there seems to be a **DEEP DARK HOLE** in the place of my brain where other people store how docker paths work, here is a quick reminder:

In the `source` argument **trailing slashes are irrelevant** - only the contents of the specified directory are copied, never the directory itself. 
In the `destination` argument the trailing slash (sometimes) matters. If you want to ensure the destination is a directory you must use a trailing slash.

## Example 
As it is easier if we can look at what happens, here is an example:
Here is the file tree of the docker context:
{% include img.html src='docker_context.png' alt='My imagge' caption='The docker directory' %}

### The docker file

```docker
FROM python:3.13

WORKDIR /app

# --- source directory --- #

# source with slash
COPY src/ ./copied_with_slash
# source without slash
COPY src ./copied_without_slash


# destination with slash
COPY src ./dest_slash/
# destination without slash
COPY src ./without_dest_slash

# --- source file --- # 

# destination without slash - assumes the destination is a file 
COPY README.md /app/single_file_without_slash
# with slash - assumes destination is dir - source file name is preserved
COPY README.md /app/single_file_with_slash/

CMD ["bash"]
```

### Container file structure
The resulting file structure in the container:

{% include img.html src='container_file_structure.png' alt='My imagge' caption='The docker directory' %}

Pay attention to what happens when you copy a single file but dont use a trailing slash in the `destination` argument. Docker assumes the destination is a file and stores the content of the README.md in that file.

The code for this example can be found [here](https://github.com/abelinglars/docker_file_paths) to peruse at your leisure.
