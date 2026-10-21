# Shell permissions
0-iam_betty: Switches to user betty.
1-who_am_i : Prints effective username.
2-groups : Prints current user's groups.
3-new_owner : Changes owner of hello to betty.
4-empty : Create empty file named hello.
5-execute : Execute permission for owner.
6-multiple_permissions : Add execute for owner and group, and read for others.
7-everybody : Add execute for everyone.
8-James_Bond : owner:none, group:none, others:everything.
9-John_Doe : set rwxr-x-wx.
10-mirror_permissions : copy olleh's permissions onto hello.
11-directories_permissions : execute for everyone to the immediate subdir.
12-directory_permissions : create my_dir with 751 permissions.
13-change_group : Change hello's group to school.
14-change_owner_and_group : Change owner to vincent and the group owner to staff for all the files and directories in the working directory.
15-symbolic_link_permissions : change owner of symbolic link _hello._
16-if_only: changes hello's owner to vincent only if owned by guillaume.
