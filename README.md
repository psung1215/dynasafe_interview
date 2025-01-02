# dynasafe_interview
For uploading codes about dynasafe interview

### 時間關係來不及做完
只做到 5. 安裝 Grafana 在kind叢集外，以docker或podman 執行，datasouce指向 Prometheus 儀錶板 panel 還沒配置

### 進度
1. 請以kind (https://kind.sigs.k8s.io/) 架設一個3個control-plane 節點，以及4個worker 節點 。
![image](https://github.com/user-attachments/assets/5dd6f218-01f3-434c-904c-24c9f6337c77)

2. 節點分為2群角色或功能:
   Infra node: 4個worker中的2個節點 作為infra node。
   Application node: 4 個worker 中的2 個節點 作為 application node。

我加上 role label 來區分:
![image](https://github.com/user-attachments/assets/111f1933-da6a-4c33-a7e7-756598863451)

3 . 安裝 MetalLB ，以L2 模式安裝，speaker 部署在 infra node上。
![image](https://github.com/user-attachments/assets/b03586da-316e-4826-bcde-8117ff873a8c)

4. 安裝 Prometheus, node exporter, kube-state-metrics 在infra node 節點上，Prometheus 收集node exporter, kube-state-metrics的效能數據。
![image](https://github.com/user-attachments/assets/21ee42dd-8a3a-4819-bdb4-66c12e6f29f9)

5. 安裝 Grafana 在kind叢集外，以docker或podman 執行，datasouce指向 Prometheus，並呈現3個效能監控儀表板。
![image](https://github.com/user-attachments/assets/839f3dea-ed5a-4fcb-b56a-5f76949b1c9e)

>> Grafana 的部分算是不熟，HPA 也了解到概念而已還沒有實作經驗。
