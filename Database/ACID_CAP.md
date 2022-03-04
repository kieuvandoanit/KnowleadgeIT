# PHÂN BIỆT TÍNH ACID & CAP

## Transaction và ACID

##### Transaction

- Database transaction là một chuỗi bao gồm nhiều hành động khác nhau thực hiện trên cơ sở dữ liệu, các hành động này có mối quan hệ mật thiết lẫn nhau và được xem như một đơn vị duy nhất.
  -- Ví dụ: A chuyển tiền cho B: Ta thấy có 2 hành động cần làm: Trừ tiền trong tài khoản của A và cộng tiền trong tài khoản của B. Thì 2 hành động này được coi là 1 transaction vì nó có mối quan hệ mật thiết với nhau.

##### ACID

- ACID là tính chất trong đó bao gồm tập hợp của 4 đặc tính khác nhau áp dụng cho một database transaction. 4 đặc tính bao gồm: **Atomicity** (nguyên tử), **Consistency** (nhất quán), **Isolation** (độc lập) và **Durability** (bền vững).

  - Tính nguyên tử (`Atomicity`)
    Tính nguyên tử quy định rằng tất cả các hành động của một transaction cần được thực hiện thành công hoặc ngược lại nếu có 1 hành động không được thực hiện thì sẽ không có bất cơ hành động nào khác được thực hiện thành công.

  - Tính nhất quán (`Consitency`)
    Tính nhất quán quy định tại bất kì thời điểm nào, trước hoặc sau 1 transaction được thực hiện dù lỗi hay không lỗi, thì database vẫn phải được giữ ở trạng thái hợp lệ (ví dụ dữ liệu phải phù hợp với các quy định được định nghĩa cho database).

  - Tính độc lập (`Isolation`)
    Quy định từng transaction khác nhau cần phải được thực hiện trong một môi trường độc lập, nếu có 2 transaction diễn ra cùng 1 thời điểm thì cần một cơ chế đảm bảo transaction này không ảnh hưởng tới transaction khác.
  - Tính bền vững (`Consistency`)
    Quy định khi transaction được diễn ra (thành công hoặc rollback lại khi có lỗi) thì sau đó dù có bất cứ sự cố nào diễn ra với database thì khi được khôi phục lại thì dữ liệu được khôi phục sẽ giữ nguyên trạng thái trước khi có sự cố.

## Định lý CAP

- Định lý **CAP** được phát biểu dành cho các hệ thống phân tán - cụ thể là, một hệ thống phân tán chỉ có thể có được hai trong ba đặc tính mong muốn: Tính nhất quán (`Consistency`), tính khả dụng (`Availibility`) và dung sai phân vùng (`Partition tolerance`). Hệ thống phân tán là một mạng lưu trữ dữ liệu trên nhiều node (máy vật lý hoặc máy ảo) cùng một lúc. Bởi vì tất cả các ứng dụng đám mây đều là hệ thống phân tán, khi thiết kế ứng dụng đám mây, chúng ta cần phải hiểu định lý `CAP` để có thể lựa chọn hệ thống quản lý dữ liệu với các đặc điểm mà ứng dụng của chúng ta cần nhất.
  - Tính nhất quán: Tại cùng một thời điểm, dữ liệu mà tất cả các máy khách nhìn thấy phải là giống nhau, bất kể nối với node nào. Để điều này xảy ra, bất cứ khi nào dữ liệu được khi vào một node, nó phải được chuyển tiếp hoặc sao chép ngay lập tức tới tất cả các node khác trong hệ thống trước khi việc ghi được coi là "thành công".
  - Tính khả dụng: Bất kì máy khác nào đưa ra yêu cầu dữ liệu đều nhận được phản hồi, ngay cả khi một hoặc nhiều node bị ngừng hoạt động. Hay nói cách khác - đối với bất kỳ yêu cầu nào, tất cả các node đang hoạt động trong hệ thống phân tán phải trả về phản hồi hợp lệ.
  - Dung sai phân vùng: Phân vùng là sự đứt gãy liên lạc trong hệ thống phân tán. Không giống như các CSDL SQL có thể scale theo chiều dọc, cơ sở dữ liệu NoSQL được thiết kế để có thể scale theo chiều ngang phân tán, tức có thể mở rộng nhanh chóng trên một mạng lớn dần bao gồm nhiều node được kết nối với nhau.
- Các cơ sở dữ liệu NoSQL được phân loại dựa trên các đặc điểm trong định lý CAP mà chúng hỗ trợ:
  - Cở sở dữ liệu CP: Một CSDL CP có tính nhất quán và dung sai phân vùng, tức hi sinh tính khả dụng. Khi tình trạng phân vùng xảy ra giữa 2 node bất kỳ, hệ thống phải shutdown node gặp tình trạng không nhất quán (tức là làm cho nó không khả dụng) cho đến khi phân vùng được giải quyết.
  - Cơ sở dữ liệu AP: cung cấp tính khả dụng và khả năng chịu phân vùng với chi phí nhất quán. Khi tình trạng phân vùng xảy ra, tất cả các node vẫn có khả dụng nhưng sẽ có những node chứa phiên bản dữ liệu cũ hơn những node khác.
  - Cơ sở dữ liệu CA: Cơ sở dữ liệu CA cung cấp tính nhất quán và tính khả dụng trên tất cả các node. Tuy nhiên, nó không thể thực hiện đc điều này nếu xảy ra tình trạng phân vùng giữa 2 node bất kỳ trong hệ thống và do đó không có khả năng chịu lỗi. (Trong hệ thống phân tán, việc bị phân vùng là không thể tránh khỏi. Vì vậy, chúng ta có thể thảo luận về CSDL phân tán CA về mặt lý thuyết, trên thực tế CSDL phân tán CA không thể tồn tại. Tuy nhiên, điều này không có nghĩa là chúng ta không thể tạo 1 CSDL CA khi xây dựng một ứng dụng phân tán. Nhiều CSDL quan hệ, chằng hạn như Postgre cung cấp tính nhất quán và tính khả dụng và có thể được deploy lên nhiều node bằng cách nhân bản.)
- Một số ví dụ:
  - MongoDB: MongoDB lưu trữ dữ liệu dưới dạng tài liệu BSON (JSON nhị phân) Nó thường được sử dụng cho dữ liệu lớn và các ứng dụng thời gian thực chạy ở nhiều vị trí khác nhau. MongoDB là một kho lưu trữ dữ liệu CP - nó giải quyết các phân vùng mạng bằng cách duy trì tính nhất quán, nhưng không đảm bảo tính khả dụng. MongoDB là hệ thống `single-master` -> mỗi tập hợp bản sao chỉ có thể có 1 node chính tiếp nhận tất cả các thao tác bản ghi. Tất cả các node khác trong cùng 1 tập hợp bản sao là các node thứ cấp log lại nhật kí hoạt động của node chính và áp dụng các hoạt động đó vào tập dữ liệu của riêng chúng. Mặc định, các máy khách cũng đọc từ node chính, nhưng cũng có thể tùy chỉnh để các máy khách có thể đọc từ các node phụ. Khi node chính không hoạt động, node phụ có nhật kí hoạt động gần đây nhất sẽ được chọn làm node chính mới. Khi tất cả các node phụ khác bắt kịp với node chính mới, cụm sẽ khả dụng trở lại.
  - Cassandra và định lý CAP (AP): Apache Cassandra là một CSDL NoSQL mã nguồn mở được maintain bởi Apache Software Foundation. Đây là một cơ sở dữ liệu dạng wide-column cho phép lưu trữ dữ liệu trên mạng phân tán. Tuy nhiên, không giống như MongoDB, Cassandra có kiến trúc `Masterless` và kết quả là có nhiều điểm có thể gặp lỗi chứ không phải một điểm duy nhất. Cassandra là một cơ sở dữ liệu AP - cung cấp tính khả dụng và dung sai phân vùng nhưng không thể cung cấp tính nhất quán mọi lúc. Bởi vì, cassandra không có node chính, tất cả node phải có sẵn liên tục. Tuy nhiên, Cassandra cung cấp tính nhất quán cuối cùng bằng cách cho phép máy khách ghi vào bất kì node nào vào bất kỳ lúc nào và điều chỉnh các confilic càng nhanh càng tốt.
