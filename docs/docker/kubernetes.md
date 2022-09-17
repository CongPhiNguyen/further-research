---
sidebar_position: 6
---

# Kubernetes

## Khái niệm

- Là một standard, một framework để làm container orchestration tức là điều phối, quản lý các container sao cho chúng chạy hiệu quả nhất, large scale không cần phụ thuộc vào cái cloud provider.
- Với các hỗ trợ:
  - Auto deploy
  - Scaling, Load Balancing,
  - Management
- Là docker compose cho việc deploy. Nhưng mà tiện lợi hơi cho việc quản lý các container

## Tại sao phải sử dụng

- Bởi vì khi mà chạy nhiều container thì có thể 1 container vì gì đó bị stop mà ko start lại dẫn đến ứng dụng không thể sử dụng được
- Kiểu cũng phải tính tới trường hợp nhận nhiều request quá dẫn đến ko handle kịp
- Có thể nâng cao số lượng container của 1 service để mà chạy luôn
- ECS có hỗ trợ nhưng cũng không tốt bằng Kubernetes

## Cách sử dụng

- Phải có file config
- Dùng nó cho tất cả cloud provider

## Cấu tạo

- Gồm nhiều worker node
  - Bao gồm: 1 proxy/config và 1 pod
  - 1 pod có thể gồm nhiều container, nó sẽ có các resource được share chung, và 1 cluster internal IP
  - Mỗi cái sẽ có 1 kubelet và 1 docker riêng
    - Kubelet dùng để tương tác với Master node
- Tất cả worker node quản lý bởi masternode
  - Bao gồm:
    - API Server dùng để kết nối với Kubelet
    - Scheduler dùng để watch các Pods, chọn Pod để chạy
    - Kube controller manager: watches, chạy các Worker node, chỉnh sửa số lượng các
    - Cloud-controller Manager: dùng để tương tác khi chạy trên các cloud
  - Có thể được split để khi cái worker toang thì nó vẫn còn
- Mình chỉ cần cung cấp file config thôi là chạy ok

- Kubernetes hoạt động với các object: Pod, Deployment, Service, Volume

## Một số khái niệm khác

- Cluster: Các Node machine chạy app hoặc chạy trình quản lý các app(Worker node và master node)
- Node: Physic hoặc virtual machine để chạy 1 hoặc nhiều pod và tương tác với container
- Services: 1 set của các Pod, mỗi cái có IP khác nhau
  - Quản lý hơi khó do mỗi cái mỗi IP khác nhau, do vậy nó group lại thành các shared API.
  - Expose để mà chạy:
    - `kubectl expose deployment first-app --type=LoadBalancer --port=8000`
      - Là loadbalancer để mà nó hỗ trợ được expose với ip các kiểu hơn so với các option khác
    - `kubectl get pods`: Xem các pod
    - `kubectl get services`: Xem các services
    - Chạy get services nếu thấy đang pending thì có thể chạy `minikube service first-app` để mà lấy cái ip chạy cái firstapp

## Các tính năng

## Cài đặt

- Kubectl:
  - Cài đặt: `kubectl --output=yaml version`
- Minikube:

  - Chạy: `minikube start drive=docker` ngoài docker ra nó còn hiện cho mình nhiều option khác, có thể chọn ssh, virtualbox
  - Kiểm tra: `minikube status` để xem thông tin, `minikube dashboard` có cái web để mình quản lý luôn

- Chạy 1 deployment:
  - `kubectl create deployment first-app --image=<image-name>`
