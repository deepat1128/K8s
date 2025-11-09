
# Upgrade the release
helm upgrade myhelloworld ./helloworld --namespace deepa -f values.yaml
#This reads the updated service type (LoadBalancer) from values.yaml.


#Helm updates the service in the cluster.
#Get an external IP
kubectl get svc myhelloworld -n deepa -w

#Get the endpoint
export SERVICE_IP=$(kubectl get svc myhelloworld -n deepa -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
echo http://$SERVICE_IP:80
#This will print the URL you can open in a browser or curl.

http://externalIP:80
curl http://externalIP:80



