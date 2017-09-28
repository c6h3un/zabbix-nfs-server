# Zabbix Template - NFS v4 server
This is a zabbix 3.0 template for nfs v4 server statistics.  
Gathering items as we can list nfs statistics using following commands on the nfs server side.

```
$ nfsstat -4 -s
---
Server rpc stats:
calls      badcalls   badclnt    badauth    xdrcall
423843     0          0          0          0

Server nfs v4:
null         compound
12        0% 423831   99%

Server nfs v4 operations:
op0-unused   op1-unused   op2-future   access       close        commit
0         0% 0         0% 0         0% 16178     2% 8598      1% 0         0%
create       delegpurge   delegreturn  getattr      getfh        link
703       0% 0         0% 4555      0% 137050   20% 22079     3% 0         0%
lock         lockt        locku        lookup       lookup_root  nverify
0         0% 0         0% 0         0% 12159     1% 0         0% 0         0%
open         openattr     open_conf    open_dgrd    putfh        putpubfh
9075      1% 0         0% 295       0% 0         0% 155165   23% 0         0%
putrootfh    read         readdir      readlink     remove       rename
4038      0% 3535      0% 2560      0% 0         0% 5199      0% 277       0%
renew        restorefh    savefh       secinfo      setattr      setcltid
258611   38% 0         0% 277       0% 0         0% 16249     2% 3147      0%
setcltidconf verify       write        rellockowner bc_ctl       bind_conn
3147      0% 0         0% 3201      0% 0         0% 0         0% 0         0%
exchange_id  create_ses   destroy_ses  free_stateid getdirdeleg  getdevinfo
0         0% 0         0% 0         0% 0         0% 0         0% 0         0%
getdevlist   layoutcommit layoutget    layoutreturn secinfononam sequence
0         0% 0         0% 0         0% 0         0% 0         0% 0         0%
set_ssv      test_stateid want_deleg   destroy_clid reclaim_comp
0         0% 0         0% 0         0% 0         0% 0         0%
---
$ nfsstat -l
---
nfs v4 server        total:   423843
------------- ------------- --------
nfs v4 server         null:       12
nfs v4 server     compound:   423831

nfs v4 servop        total:   666098
------------- ------------- --------
nfs v4 servop       access:    16178
nfs v4 servop        close:     8598
nfs v4 servop       create:      703
nfs v4 servop  delegreturn:     4555
nfs v4 servop      getattr:   137050
nfs v4 servop        getfh:    22079
nfs v4 servop       lookup:    12159
nfs v4 servop         open:     9075
nfs v4 servop    open_conf:      295
nfs v4 servop        putfh:   155165
nfs v4 servop    putrootfh:     4038
nfs v4 servop         read:     3535
nfs v4 servop      readdir:     2560
nfs v4 servop       remove:     5199
nfs v4 servop       rename:      277
nfs v4 servop        renew:   258611
nfs v4 servop       savefh:      277
nfs v4 servop      setattr:    16249
nfs v4 servop     setcltid:     3147
nfs v4 servop setcltidconf:     3147
nfs v4 servop        write:     3201
---
```

## Usage
1. put the *zabbix-nfs-server.conf* under `/etc/zabbix/zabbix_agentd.conf.d/` and restart service
2. import *nfs-v4-server.xml* to zabbix server
3. Checking if getting data, then all done.

## References 
- http://elixir.free-electrons.com/linux/latest/source/Documentation/filesystems/nfs/knfsd-stats.txt
- https://www.svennd.be/nfsd-stats-explained-procnetrpcnfsd/
