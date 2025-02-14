# Deploy Ứng Dụng Lên Kubernetes

## 1. Yêu Cầu Hệ Thống
Trước khi bắt đầu, hãy đảm bảo bạn đã cài đặt các công cụ sau trên máy:
- [Docker](https://docs.docker.com/get-docker/)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)

## 2. Clone Repository
Clone dự án từ GitHub:
```sh
git clone https://github.com/doanndev/demo-kubernetes.git
cd demo-kubernetes
```

## 3. Chạy Minikube
Khởi động Minikube cluster:
```sh
minikube start
```
Kiểm tra node đã hoạt động chưa:
```sh
kubectl get nodes
```

## 4. Deploy Ứng Dụng Lên Kubernetes
### 4.1. Tạo Deployment & Service
Triển khai ứng dụng bằng các file YAML:
```sh
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```
Kiểm tra pod và service đã chạy chưa:
```sh
kubectl get pods
kubectl get svc
```

### 4.2. Truy Cập Ứng Dụng
Lấy địa chỉ truy cập ứng dụng:
```sh
minikube service my-app-service
```
Hoặc:
```sh
kubectl get svc my-app-service
```
Sau đó mở trình duyệt và truy cập `http://<Minikube_IP>:<NodePort>`.

## 5. Debugging (Nếu Có Lỗi)
Nếu có lỗi, kiểm tra trạng thái pod:
```sh
kubectl get pods
kubectl describe pod <pod-name>
kubectl logs <pod-name>
```
Nếu cần restart Minikube:
```sh
minikube delete
minikube start
```

## 6. Xóa Ứng Dụng (Nếu Cần)
Nếu bạn muốn gỡ bỏ ứng dụng:
```sh
kubectl delete deployment chating-app
kubectl delete svc chating-app-service
```

🚀 **Ứng dụng đã được triển khai thành công!**

