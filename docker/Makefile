
create-key:
	hzn key create IBM glendarling@us.ibm.com

publish-service:
	hzn exchange service publish -O -f service.json --pull-image

publish-pattern:
	hzn exchange pattern publish -f pattern.json

publish-biz:
	hzn exchange business addpolicy -f docker_biz.json ibm.mosquito.biz.docker

register-pattern:
	hzn register --pattern pattern.ibm.mosquito.facemask.docker

register-policy:
	hzn register --policy docker_node.json

test:
	curl -sS localhost:5001/test; echo

cleanup:
	-sudo hzn unregister -frDv 2>/dev/null || :
	-hzn exchange pattern remove -f mycluster/pattern.ibm.mosquito.facemask.docker 2>/dev/null || :
	-hzn exchange business removepolicy -f mycluster/ibm.mosquito.biz.docker 2>/dev/null || :
	-hzn exchange service remove -f mycluster/ibm.mosquito.facemask.docker 2>/dev/null || :
	-rm -rf /home/zen/.hzn/keys
