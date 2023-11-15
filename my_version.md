# complete installation of ansible

- step 1 . create a proj directory

``` bash
mkdir proj
```

- step 2. create a main yaml file and add the following content

```bash
touch main.yml
```

```yaml
---
- name: My Playbook
  hosts: localhost
  connection: local
  become: true
  roles:
    - my_role
```


- step 3. create roles
```bash
ansible-galaxy init my_role
```

- step 4. navigate into the roles/files directory
```bash
cd /proj/my_role/files/
touch my_file.txt
```
now write something of you choice 

now navigate to tasks folder

```bash
cd ../tasks/
```
```bash
nano main.yml
```
and paste the following 
```yaml
---
# tasks file for my_role

- name: Ensure a directory exists
  ansible.builtin.file:
    path: /home/ec2-user/new_directory/
    state: directory

- name: Copy a file
  ansible.builtin.copy:
    src: files/my_file.txt
    dest: /home/ec2-user/new_directory/my_file.txt
```

- step 5. play the playbook
```bash
ansible-playbook main.yml
```

- step 6. verify the created directory outside the current

