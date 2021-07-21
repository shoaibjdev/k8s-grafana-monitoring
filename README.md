# k8s-grafana-monitoring
Detailed Kubernetes Dashboard for Monitoring
---

### 1. Create Kubernetes Objects
1.  kubectl create namespace ops-monit
2.  kubectl apply -f kube-state-metrics/
3.  kubectl apply -f kube-prometheus
4.  watch kubectl -n ops-monit get all


Every 2.0s: kubectl -n ops-monit get all                        

      NAME                                         READY   STATUS    RESTARTS   AGE
      pod/kube-state-metrics-6fb96b76cb-plvcr      1/1     Running   0          156m
      pod/prometheus-deployment-599bbd9457-zw7g4   1/1     Running   0          118m

      NAME                         TYPE        CLUSTER-IP	 EXTERNAL-IP   PORT(S)             AGE
      service/kube-state-metrics   ClusterIP   None            <none>        8080/TCP,8081/TCP   117m
      service/prometheus-service   NodePort    10.233.54.231   <none>        8080:**30000**/TCP	   115m

      NAME                                    READY   UP-TO-DATE   AVAILABLE   AGE
      deployment.apps/kube-state-metrics	1/1     1            1           156m
      deployment.apps/prometheus-deployment   1/1     1            1           129m

      NAME                                               DESIRED   CURRENT   READY   AGE
      replicaset.apps/kube-state-metrics-6fb96b76cb	   1         1         1       156m
      replicaset.apps/prometheus-deployment-599bbd9457   1         1         1       129m
  
  

### 2. Create Prometheus DataSource on Grafana 
`Point Prometheus to NodePort for Prometheus service -- http://<NODE-IP>:**30000**`
  
  
### 3. Upload Dashboard JSON to Grafana and Choose Prometheus DataSource created in Step 2  
  
    Grafana Dashboard JSON: kubernetes-for-prometheus-dashboard-en-SRK.json  

