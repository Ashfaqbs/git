## 🧠 Git Workflow Issue + Fix (eg: Flink v2 Flow)

### 🧨 **Issue**
While working on the Flink v2 integration, I accidentally added a bunch of unwanted files into Git. This included:

- `.idea/` (IntelliJ IDE configs)
- `target/` (compiled classes & JARs)
- Backup/temp files like `*.log~`, `*.md~`, etc.

These got staged and even committed by mistake.

---

### 🔍 **How It Was Caught**
Ran:
```bash
git status
```
Saw a lot of junk files in the commit — realized they shouldn’t be in the repo. Luckily, I hadn’t pushed yet.

---

### 🛠️ **Fix Steps**
To fix it cleanly **without losing work**, I did the following:

1. **Rollback last commit but keep all changes staged:**
   ```bash
   git reset --soft HEAD~1
   ```

2. **Unstage all files:**
   ```bash
   git restore --staged .
   ```

3. **Stage only the files I actually wanted to commit:**
   ```bash
   git add code/java/flink-2.0/my-flink-project/pom.xml
   git add code/java/flink-2.0/my-flink-project/src/
   ```

4. **Commit the clean changes:**
   ```bash
   git commit -m "Add Flink v2 simple flows"
   ```

5. **Push to remote:**
   ```bash
   git push
   ```

---

### ✅ **Result**
Repo now contains only the intended Flink v2 project files:
- `pom.xml`
- Java source code inside `src/main/java/com/example/`

No IDE, target, or temp files were pushed to GitHub 

---


- Raw git activites for reference

```
C:\tmp>git clone https://github.com/Ashfaqbs/Apache-Flink.git
Cloning into 'Apache-Flink'...
remote: Enumerating objects: 172, done.
remote: Counting objects: 100% (172/172), done.
remote: Compressing objects: 100% (115/115), done.
remote: Total 172 (delta 44), reused 155 (delta 29), pack-reused 0 (from 0)
Receiving objects: 100% (172/172), 23.43 MiB | 3.83 MiB/s, done.
Resolving deltas: 100% (44/44), done.

C:\tmp>cd Apache-Flink

C:\tmp\Apache-Flink>git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   code/java/flink-2.0/docker/docker-composev2.0.yml

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        code/java/flink-2.0/my-flink-project/

no changes added to commit (use "git add" and/or "git commit -a")

C:\tmp\Apache-Flink>git add  code/java/flink-2.0/my-flink-project/
warning: in the working copy of 'code/java/flink-2.0/my-flink-project/.idea/material_theme_project_new.xml', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'code/java/flink-2.0/my-flink-project/.idea/vcs.xml', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'code/java/flink-2.0/my-flink-project/docker-compose.yml', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'code/java/flink-2.0/my-flink-project/target/maven-status/maven-compiler-plugin/compile/default-compile/createdFiles.lst', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'code/java/flink-2.0/my-flink-project/target/maven-status/maven-compiler-plugin/testCompile/default-testCompile/createdFiles.lst', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'code/java/flink-2.0/my-flink-project/target/surefire-reports/TEST-com.example.AppTest.xml', LF will be replaced by CRLF the next time Git touches it

C:\tmp\Apache-Flink>git commit -m "Add flink 2 simple flows"
[main 1ec9faa] Add flink 2 simple flows
 37 files changed, 2705 insertions(+)
 create mode 100644 code/java/flink-2.0/my-flink-project/.idea/.gitignore
 create mode 100644 code/java/flink-2.0/my-flink-project/.idea/compiler.xml
 create mode 100644 code/java/flink-2.0/my-flink-project/.idea/jarRepositories.xml
 create mode 100644 code/java/flink-2.0/my-flink-project/.idea/material_theme_project_new.xml
 create mode 100644 code/java/flink-2.0/my-flink-project/.idea/misc.xml
 create mode 100644 code/java/flink-2.0/my-flink-project/.idea/vcs.xml
 create mode 100644 code/java/flink-2.0/my-flink-project/docker-compose.yml
 create mode 100644 code/java/flink-2.0/my-flink-project/output/FlinkSimpleJob/img.png
 create mode 100644 code/java/flink-2.0/my-flink-project/output/FlinkSimpleJob/op.md
 create mode 100644 code/java/flink-2.0/my-flink-project/output/SimpleWindowingJob/img.png
 create mode 100644 code/java/flink-2.0/my-flink-project/output/SimpleWindowingJob/op.md
 create mode 100644 code/java/flink-2.0/my-flink-project/output/SimpleWindowingJob/op.md~
 create mode 100644 code/java/flink-2.0/my-flink-project/output/jar1.log~
 create mode 100644 code/java/flink-2.0/my-flink-project/output/jar1.md~
 create mode 100644 code/java/flink-2.0/my-flink-project/pom.xml
 create mode 100644 code/java/flink-2.0/my-flink-project/src/main/java/com/example/App.java
 create mode 100644 code/java/flink-2.0/my-flink-project/src/main/java/com/example/FlinkSimpleJob.java
 create mode 100644 code/java/flink-2.0/my-flink-project/src/main/java/com/example/SimpleWindowingJob.java
 create mode 100644 code/java/flink-2.0/my-flink-project/target/classes/com/example/App.class
 create mode 100644 code/java/flink-2.0/my-flink-project/target/classes/com/example/CheckpointExample.java~
 create mode 100644 code/java/flink-2.0/my-flink-project/target/classes/com/example/CheckpointingExampleJob.java~
 create mode 100644 code/java/flink-2.0/my-flink-project/target/classes/com/example/FlinkSimpleJob$1.class
 create mode 100644 code/java/flink-2.0/my-flink-project/target/classes/com/example/FlinkSimpleJob.class
 create mode 100644 code/java/flink-2.0/my-flink-project/target/classes/com/example/FlinkSimpleJob.java~
 create mode 100644 code/java/flink-2.0/my-flink-project/target/classes/com/example/SimpleWindowingJob$SimpleEventSource.class
 create mode 100644 code/java/flink-2.0/my-flink-project/target/classes/com/example/SimpleWindowingJob.class
 create mode 100644 code/java/flink-2.0/my-flink-project/target/classes/com/example/StatefulFlinkJob.java~
 create mode 100644 code/java/flink-2.0/my-flink-project/target/classes/com/example/WordCountWithCheckpoints.java~
 create mode 100644 code/java/flink-2.0/my-flink-project/target/maven-archiver/pom.properties
 create mode 100644 code/java/flink-2.0/my-flink-project/target/maven-status/maven-compiler-plugin/compile/default-compile/createdFiles.lst
 create mode 100644 code/java/flink-2.0/my-flink-project/target/maven-status/maven-compiler-plugin/compile/default-compile/inputFiles.lst
 create mode 100644 code/java/flink-2.0/my-flink-project/target/maven-status/maven-compiler-plugin/testCompile/default-testCompile/createdFiles.lst
 create mode 100644 code/java/flink-2.0/my-flink-project/target/maven-status/maven-compiler-plugin/testCompile/default-testCompile/inputFiles.lst
 create mode 100644 code/java/flink-2.0/my-flink-project/target/my-flink-project-1.0-SNAPSHOT.jar
 create mode 100644 code/java/flink-2.0/my-flink-project/target/surefire-reports/TEST-com.example.AppTest.xml
 create mode 100644 code/java/flink-2.0/my-flink-project/target/surefire-reports/com.example.AppTest.txt
 create mode 100644 code/java/flink-2.0/my-flink-project/target/test-classes/com/example/AppTest.class

C:\tmp\Apache-Flink>git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   code/java/flink-2.0/docker/docker-composev2.0.yml

no changes added to commit (use "git add" and/or "git commit -a")


- Rollback last commit but keep all changes staged

C:\tmp\Apache-Flink>git reset --soft HEAD~1

C:\tmp\Apache-Flink>git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   code/java/flink-2.0/my-flink-project/.idea/.gitignore
        new file:   code/java/flink-2.0/my-flink-project/.idea/compiler.xml
        new file:   code/java/flink-2.0/my-flink-project/.idea/jarRepositories.xml
        new file:   code/java/flink-2.0/my-flink-project/.idea/material_theme_project_new.xml
        new file:   code/java/flink-2.0/my-flink-project/.idea/misc.xml
        new file:   code/java/flink-2.0/my-flink-project/.idea/vcs.xml
        new file:   code/java/flink-2.0/my-flink-project/docker-compose.yml
        new file:   code/java/flink-2.0/my-flink-project/output/FlinkSimpleJob/img.png
        new file:   code/java/flink-2.0/my-flink-project/output/FlinkSimpleJob/op.md
        new file:   code/java/flink-2.0/my-flink-project/output/SimpleWindowingJob/img.png
        new file:   code/java/flink-2.0/my-flink-project/output/SimpleWindowingJob/op.md
        new file:   code/java/flink-2.0/my-flink-project/output/SimpleWindowingJob/op.md~
        new file:   code/java/flink-2.0/my-flink-project/output/jar1.log~
        new file:   code/java/flink-2.0/my-flink-project/output/jar1.md~
        new file:   code/java/flink-2.0/my-flink-project/pom.xml
        new file:   code/java/flink-2.0/my-flink-project/src/main/java/com/example/App.java
        new file:   code/java/flink-2.0/my-flink-project/src/main/java/com/example/FlinkSimpleJob.java
        new file:   code/java/flink-2.0/my-flink-project/src/main/java/com/example/SimpleWindowingJob.java
        new file:   code/java/flink-2.0/my-flink-project/target/classes/com/example/App.class
        new file:   code/java/flink-2.0/my-flink-project/target/classes/com/example/CheckpointExample.java~
        new file:   code/java/flink-2.0/my-flink-project/target/classes/com/example/CheckpointingExampleJob.java~
        new file:   code/java/flink-2.0/my-flink-project/target/classes/com/example/FlinkSimpleJob$1.class
        new file:   code/java/flink-2.0/my-flink-project/target/classes/com/example/FlinkSimpleJob.class
        new file:   code/java/flink-2.0/my-flink-project/target/classes/com/example/FlinkSimpleJob.java~
        new file:   code/java/flink-2.0/my-flink-project/target/classes/com/example/SimpleWindowingJob$SimpleEventSource.class
        new file:   code/java/flink-2.0/my-flink-project/target/classes/com/example/SimpleWindowingJob.class
        new file:   code/java/flink-2.0/my-flink-project/target/classes/com/example/StatefulFlinkJob.java~
        new file:   code/java/flink-2.0/my-flink-project/target/classes/com/example/WordCountWithCheckpoints.java~
        new file:   code/java/flink-2.0/my-flink-project/target/maven-archiver/pom.properties
        new file:   code/java/flink-2.0/my-flink-project/target/maven-status/maven-compiler-plugin/compile/default-compile/createdFiles.lst
        new file:   code/java/flink-2.0/my-flink-project/target/maven-status/maven-compiler-plugin/compile/default-compile/inputFiles.lst
        new file:   code/java/flink-2.0/my-flink-project/target/maven-status/maven-compiler-plugin/testCompile/default-testCompile/createdFiles.lst
        new file:   code/java/flink-2.0/my-flink-project/target/maven-status/maven-compiler-plugin/testCompile/default-testCompile/inputFiles.lst
        new file:   code/java/flink-2.0/my-flink-project/target/my-flink-project-1.0-SNAPSHOT.jar
        new file:   code/java/flink-2.0/my-flink-project/target/surefire-reports/TEST-com.example.AppTest.xml
        new file:   code/java/flink-2.0/my-flink-project/target/surefire-reports/com.example.AppTest.txt
        new file:   code/java/flink-2.0/my-flink-project/target/test-classes/com/example/AppTest.class

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   code/java/flink-2.0/docker/docker-composev2.0.yml


-- Unstage all files

C:\tmp\Apache-Flink>git restore --staged .

C:\tmp\Apache-Flink>git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   code/java/flink-2.0/docker/docker-composev2.0.yml

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        code/java/flink-2.0/my-flink-project/

no changes added to commit (use "git add" and/or "git commit -a")

C:\tmp\Apache-Flink>git add code/java/flink-2.0/my-flink-project/pom.xml

C:\tmp\Apache-Flink>git add code/java/flink-2.0/my-flink-project/src/

C:\tmp\Apache-Flink>git commit -m "Add Flink v2 simple flows"
[main 582bef1] Add Flink v2 simple flows
 4 files changed, 146 insertions(+)
 create mode 100644 code/java/flink-2.0/my-flink-project/pom.xml
 create mode 100644 code/java/flink-2.0/my-flink-project/src/main/java/com/example/App.java
 create mode 100644 code/java/flink-2.0/my-flink-project/src/main/java/com/example/FlinkSimpleJob.java
 create mode 100644 code/java/flink-2.0/my-flink-project/src/main/java/com/example/SimpleWindowingJob.java

C:\tmp\Apache-Flink>git push
Enumerating objects: 19, done.
Counting objects: 100% (19/19), done.
Delta compression using up to 16 threads
Compressing objects: 100% (11/11), done.
Writing objects: 100% (15/15), 2.72 KiB | 185.00 KiB/s, done.
Total 15 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/Ashfaqbs/Apache-Flink.git
   8bfdd44..582bef1  main -> main


```
