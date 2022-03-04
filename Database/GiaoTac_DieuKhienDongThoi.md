# GIAO TÁC - ĐIỀU KHIỂN ĐỒNG THỜI (T-SQL)

## Giao tác
- Là 1 tập hợp các thao tác có thứ tự truy xuất dữ liệu trên CSDL thành 1 đơn vị công việc logic, chuyển CSDL từ trạng thái nhất quán này sang trạng thái nhất quán khác.
## Điều khiển đồng thời
- Lý do: Đảm bảo nhiều giao tác thực hiện đồng thời mà vẫn đảm bảo tính đúng đắn trên CSDL.
![](../images/dkdt1.png)
  - Scheduler nhận yêu cầu Read/Write từ các giao tác và điều khiển: cho thực thi hoặc chờ hoặc hủy giao tác tùy vào kỹ thuật điều khiển đồng thời được cài đặt.
**Các vấn đề của điều khiển đồng thời**
- Mất dữ liệu cập nhật (Lost update)
 - TH1:
    ![LostUpdate](../images/lostUpdate_1.png)