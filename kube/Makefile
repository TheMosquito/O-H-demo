
create-key:
	hzn key create IBM glendarling@us.ibm.com

publish-service:
	hzn exchange service publish -O -f service.json --pull-image

publish-pattern:
	hzn exchange pattern publish -f pattern.json

publish-biz:
	hzn exchange business addpolicy -f kube_biz.json ibm.mosquito.biz.kube

register-pattern:
	hzn register --pattern pattern.ibm.mosquito.facemask.kube

register-policy:
	# hzn register --policy kube_node.json
	hzn register -u iamapikey:EUjyXPVEcyYGn9ULhYhR-PGWOP6rrJJqyb0JyFEBqrDj --policy node.policy.json -v -n glen-cluster:Horiz0n

test:
	curl -sS localhost:5001/test; echo

cleanup:
	-sudo hzn unregister -frDv 2>/dev/null || :
	-hzn exchange pattern remove -f mycluster/pattern.ibm.mosquito.facemask.kube 2>/dev/null || :
	-hzn exchange business removepolicy -f mycluster/ibm.mosquito.biz.kube 2>/dev/null || :
	-hzn exchange service remove -f mycluster/ibm.mosquito.facemask.kube 2>/dev/null || :
	-rm -rf /home/zen/.hzn/keys
