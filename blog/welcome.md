<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Install MongoDB in Limux mint 18.2</title>
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__left">
    <div class="stackedit__toc">
      
    </div>
  </div>
  <div class="stackedit__right">
    <div class="stackedit__html">
      <p>lwk@qwfys ~/ $ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927<br>
[sudo] password for lwk:<br>
Executing: /tmp/tmp.AasdNL9T70/gpg.1.sh --keyserver<br>
hkp://keyserver.ubuntu.com:80<br>
–recv<br>
EA312927<br>
gpg: requesting key EA312927 from hkp server <a href="http://keyserver.ubuntu.com">keyserver.ubuntu.com</a><br>
gpg: key EA312927: public key “MongoDB 3.2 Release Signing Key <a href="mailto:packaging@mongodb.com">packaging@mongodb.com</a>” imported<br>
gpg: Total number processed: 1<br>
gpg:               imported: 1  (RSA: 1)</p>
<p>lwk@qwfys ~ $<br>
lwk@qwfys ~ $ echo “deb <a href="http://repo.mongodb.org/apt/ubuntu">http://repo.mongodb.org/apt/ubuntu</a> xenial/mongodb-org/3.2 multiverse” | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list<br>
deb <a href="http://repo.mongodb.org/apt/ubuntu">http://repo.mongodb.org/apt/ubuntu</a> xenial/mongodb-org/3.2 multiverse<br>
lwk@qwfys ~ $ apt update<br>
Hit:1 <a href="http://archive.ubuntukylin.com:10006/ubuntukylin">http://archive.ubuntukylin.com:10006/ubuntukylin</a> xenial InRelease<br>
Ign:2 <a href="http://mirrors.ustc.edu.cn/linuxmint">http://mirrors.ustc.edu.cn/linuxmint</a> sylvia InRelease<br>
Hit:3 <a href="http://mirrors.ustc.edu.cn/ubuntu">http://mirrors.ustc.edu.cn/ubuntu</a> xenial InRelease<br>
Hit:4 <a href="http://mirrors.ustc.edu.cn/ubuntu">http://mirrors.ustc.edu.cn/ubuntu</a> xenial-updates InRelease<br>
Hit:5 <a href="http://mirrors.ustc.edu.cn/ubuntu">http://mirrors.ustc.edu.cn/ubuntu</a> xenial-backports InRelease<br>
Hit:6 <a href="http://mirrors.ustc.edu.cn/linuxmint">http://mirrors.ustc.edu.cn/linuxmint</a> sylvia Release<br>
Ign:8 <a href="http://repo.mongodb.org/apt/ubuntu">http://repo.mongodb.org/apt/ubuntu</a> xenial/mongodb-org/3.2 InRelease<br>
Hit:9 <a href="http://ppa.launchpad.net/webupd8team/java/ubuntu">http://ppa.launchpad.net/webupd8team/java/ubuntu</a> xenial InRelease<br>
Get:10 <a href="http://repo.mongodb.org/apt/ubuntu">http://repo.mongodb.org/apt/ubuntu</a> xenial/mongodb-org/3.2 Release [3,462 B]<br>
Get:11 <a href="http://security.ubuntu.com/ubuntu">http://security.ubuntu.com/ubuntu</a> xenial-security InRelease [102 kB]<br>
Hit:12 <a href="http://archive.canonical.com/ubuntu">http://archive.canonical.com/ubuntu</a> xenial InRelease<br>
Get:13 <a href="http://repo.mongodb.org/apt/ubuntu">http://repo.mongodb.org/apt/ubuntu</a> xenial/mongodb-org/3.2 Release.gpg [801 B]<br>
Get:14 <a href="http://repo.mongodb.org/apt/ubuntu">http://repo.mongodb.org/apt/ubuntu</a> xenial/mongodb-org/3.2/multiverse amd64 Packages [8,905 B]<br>
Fetched 115 kB in 3s (35.2 kB/s)<br>
Reading package lists… Done<br>
Building dependency tree<br>
Reading state information… Done<br>
All packages are up to date.<br>
lwk@qwfys ~ $ apt list |grep mongo</p>
<p>WARNING: apt does not have a stable CLI interface. Use with caution in scripts.</p>
<p>jmeter-mongodb/xenial,xenial 2.11-5 all<br>
juju-mongo-tools3.2/xenial 3.2.4+ds-0ubuntu1 amd64<br>
juju-mongodb/xenial 2.4.10-0ubuntu6 amd64<br>
juju-mongodb2.6/xenial 2.6.10-0ubuntu1 amd64<br>
juju-mongodb3.2/xenial-updates 3.2.15-0ubuntu1~16.04.1 amd64<br>
libcatmandu-store-mongodb-perl/xenial,xenial 0.0403-1 all<br>
libmongo-client-dev/xenial 0.1.8-2 amd64<br>
libmongo-client-doc/xenial,xenial 0.1.8-2 all<br>
libmongo-client0/xenial 0.1.8-2 amd64<br>
libmongo-client0-dbg/xenial 0.1.8-2 amd64<br>
libmongoc-1.0-0/xenial 1.3.1-1 amd64<br>
libmongoc-dbg/xenial 1.3.1-1 amd64<br>
libmongoc-dev/xenial 1.3.1-1 amd64<br>
libmongoc-doc/xenial,xenial 1.3.1-1 all<br>
libmongodb-java/xenial,xenial 2.12.4-1 all<br>
libmongodb-perl/xenial 1.2.2-1 amd64<br>
libmongodbx-class-perl/xenial,xenial 1.030002-1 all<br>
mongodb/xenial 1:2.6.10-0ubuntu1 amd64<br>
mongodb-clients/xenial 1:2.6.10-0ubuntu1 amd64<br>
mongodb-org/xenial 3.2.18 amd64<br>
mongodb-org-mongos/xenial 3.2.18 amd64<br>
mongodb-org-server/xenial 3.2.18 amd64<br>
mongodb-org-shell/xenial 3.2.18 amd64<br>
mongodb-org-tools/xenial 3.2.18 amd64<br>
mongodb-server/xenial 1:2.6.10-0ubuntu1 amd64<br>
php-mongodb/xenial 1.1.5-1~build1 amd64<br>
puppet-module-puppetlabs-mongodb/xenial,xenial 0.7.0-1 all<br>
python-mongoengine/xenial,xenial 0.10.6-1 all<br>
python-mongoengine-doc/xenial,xenial 0.10.6-1 all<br>
python-pymongo/xenial 3.2-1build1 amd64<br>
python-pymongo-doc/xenial,xenial 3.2-1build1 all<br>
python-pymongo-ext/xenial 3.2-1build1 amd64<br>
python3-mongoengine/xenial,xenial 0.10.6-1 all<br>
python3-pymongo/xenial 3.2-1build1 amd64<br>
python3-pymongo-ext/xenial 3.2-1build1 amd64<br>
ruby-em-mongo/xenial,xenial 0.5.1-1 all<br>
ruby-mongo/xenial,xenial 1.10.0-1 all<br>
syslog-ng-mod-mongodb/xenial 3.5.6-2.1 amd64<br>
lwk@qwfys ~ $ apt install mongodb-org<br>
Reading package lists… Done<br>
Building dependency tree<br>
Reading state information… Done<br>
The following packages were automatically installed and are no longer required:<br>
dconf-cli libclutter-imcontext-0.1-0 libclutter-imcontext-0.1-bin libibus-qt1 libpango1.0-0 libpangox-1.0-0<br>
Use ‘sudo apt autoremove’ to remove them.<br>
The following additional packages will be installed:<br>
mongodb-org-mongos mongodb-org-server mongodb-org-shell mongodb-org-tools<br>
The following NEW packages will be installed:<br>
mongodb-org mongodb-org-mongos mongodb-org-server mongodb-org-shell mongodb-org-tools<br>
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.<br>
Need to get 51.7 MB of archives.<br>
After this operation, 214 MB of additional disk space will be used.<br>
Do you want to continue? [Y/n] y<br>
Get:1 <a href="http://repo.mongodb.org/apt/ubuntu">http://repo.mongodb.org/apt/ubuntu</a> xenial/mongodb-org/3.2/multiverse amd64 mongodb-org-shell amd64 3.2.18 [5,275 kB]<br>
Get:2 <a href="http://repo.mongodb.org/apt/ubuntu">http://repo.mongodb.org/apt/ubuntu</a> xenial/mongodb-org/3.2/multiverse amd64 mongodb-org-server amd64 3.2.18 [10.0 MB]<br>
Get:3 <a href="http://repo.mongodb.org/apt/ubuntu">http://repo.mongodb.org/apt/ubuntu</a> xenial/mongodb-org/3.2/multiverse amd64 mongodb-org-mongos amd64 3.2.18 [4,675 kB]<br>
Get:4 <a href="http://repo.mongodb.org/apt/ubuntu">http://repo.mongodb.org/apt/ubuntu</a> xenial/mongodb-org/3.2/multiverse amd64 mongodb-org-tools amd64 3.2.18 [31.8 MB]<br>
Get:5 <a href="http://repo.mongodb.org/apt/ubuntu">http://repo.mongodb.org/apt/ubuntu</a> xenial/mongodb-org/3.2/multiverse amd64 mongodb-org amd64 3.2.18 [3,562 B]<br>
Fetched 51.7 MB in 11s (4,514 kB/s)<br>
Selecting previously unselected package mongodb-org-shell.<br>
(Reading database … 236893 files and directories currently installed.)<br>
Preparing to unpack …/mongodb-org-shell_3.2.18_amd64.deb …<br>
Unpacking mongodb-org-shell (3.2.18) …<br>
Selecting previously unselected package mongodb-org-server.<br>
Preparing to unpack …/mongodb-org-server_3.2.18_amd64.deb …<br>
Unpacking mongodb-org-server (3.2.18) …<br>
Selecting previously unselected package mongodb-org-mongos.<br>
Preparing to unpack …/mongodb-org-mongos_3.2.18_amd64.deb …<br>
Unpacking mongodb-org-mongos (3.2.18) …<br>
Selecting previously unselected package mongodb-org-tools.<br>
Preparing to unpack …/mongodb-org-tools_3.2.18_amd64.deb …<br>
Unpacking mongodb-org-tools (3.2.18) …<br>
Selecting previously unselected package mongodb-org.<br>
Preparing to unpack …/mongodb-org_3.2.18_amd64.deb …<br>
Unpacking mongodb-org (3.2.18) …<br>
Processing triggers for man-db (2.7.5-1) …<br>
Setting up mongodb-org-shell (3.2.18) …<br>
Setting up mongodb-org-server (3.2.18) …<br>
Adding system user <code>mongodb' (UID 124) ... Adding new user</code>mongodb’ (UID 124) with group <code>nogroup' ... Not creating home directory</code>/home/mongodb’.<br>
Adding group <code>mongodb' (GID 132) ... Done. Adding user</code>mongodb’ to group `mongodb’ …<br>
Adding user mongodb to group mongodb<br>
Done.<br>
Setting up mongodb-org-mongos (3.2.18) …<br>
Setting up mongodb-org-tools (3.2.18) …<br>
Setting up mongodb-org (3.2.18) …<br>
lwk@qwfys ~ $ systemctl status mongodb<br>
● mongodb.service<br>
Loaded: not-found (Reason: No such file or directory)<br>
Active: inactive (dead)<br>
lwk@qwfys ~ $ sudo systemctl status mongod<br>
● mongod.service - High-performance, schema-free document-oriented database<br>
Loaded: loaded (/lib/systemd/system/mongod.service; disabled; vendor preset: enabled)<br>
Active: active (running) since Thu 2018-01-18 11:43:16 CST; 2h 13min ago<br>
Docs: <a href="https://docs.mongodb.org/manual">https://docs.mongodb.org/manual</a><br>
Main PID: 13494 (mongod)<br>
CGroup: /system.slice/mongod.service<br>
└─13494 /usr/bin/mongod --quiet --config /etc/mongod.conf</p>
<p>Jan 18 11:43:16 qwfys systemd[1]: Started High-performance, schema-free document-oriented database.<br>
Jan 18 13:56:35 qwfys systemd[1]: Started High-performance, schema-free document-oriented database.<br>
lwk@qwfys ~ $ sudo systemctl enable mongod<br>
Created symlink from /etc/systemd/system/multi-user.target.wants/mongod.service to /lib/systemd/system/mongod.service.<br>
lwk@qwfys ~ $</p>

    </div>
  </div>
</body>

</html>
