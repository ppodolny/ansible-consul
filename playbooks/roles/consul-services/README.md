Provision
----------
```
$ ansible-playbook -i hosts provision_consul.yaml
```

Verify the cluster
-------------------
Now you'll want to SSH into one of the Consul servers and be sure that the cluster is in the desired state. The output should look like the following:

```
$ ssh 10.0.16.4
$ consul members
Node                     Address         Status  Type    Build  Protocol
consul-server-10-0-16-4  10.0.16.4:8301  alive   server  0.3.1  2
consul-server-10-0-32-4  10.0.32.4:8301  alive   server  0.3.1  2
consul-server-10-0-48-4  10.0.48.4:8301  alive   server  0.3.1  2
```

Verify DNS lookups
--------------------
Check that Dnsmasq is successfully forwarding DNS queries to Consul. The output should look like the following:

```
$ dig consul-server-10-0-32-4.node.consul

; <<>> DiG 9.9.5-3-Ubuntu <<>> consul-server-10-0-32-4.node.consul
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 59853
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;consul-server-10-0-32-4.node.consul. IN    A

;; ANSWER SECTION:
consul-server-10-0-32-4.node.consul. 0 IN A 10.0.32.4

;; Query time: 5 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Jun 09 16:55:30 UTC 2014
;; MSG SIZE  rcvd: 104
```
