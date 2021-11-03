# Bài 1 
![1](https://user-images.githubusercontent.com/93541353/139986492-9f01c81e-78b0-48b2-bbcb-1ee0bba84fe6.PNG)
## Ý tưởng: 
* Muốn tính x^11 với số phép nhân tối thiểu cẩn có x^5 và x^6
* Để có được điều đó trước tiên cần x^3 và x^2
## Code:
```
#include <iostream>
using namespace std;

int main() {
	double x;
	cout << "nhap x ";
	cin >> x;
	//khởi tạo các biến lưu trữ các giá trị x^2,x^3,x^5
	double a, b, c;
	a = x * x;
	b = a * x;
	c = a * b;
	cout << "ket qua " << c * c * x;
	return 0;
}
```
## Mở rộng: 
Ở trên, x^11 là 1 số mũ nhỏ có thể đoán được nhưng nếu là x^100, x^1000,... thì sẽ như thế nào?
Thử 1 phép tính: 
```
		 11:	2 ta được:
		  5 dư  1 tiếp tục lấy 5 chia 2:
		  2 dư  1 lại lấy 2 chia 2:
		  1 dư  0 tới đây ta thấy muốn có x^11 trước tiên cần có x^2, sau đó là x^3, x^5, x^6.
```
Thử áp dụng với x^100: 
```
			100:	2
			50 dư   0
			25 dư   0
			12 dư   1
			6  dư   0
			3  dư   0
			1  dư   1
```
Vậy muốn tính x^11 có tổi thiểu 8 phép nhân: trước tiên cần có x^2, đến x^3, x^6, x^12, x^13, x^25, x^50 sau cùng là x^100
___
# Bài 2
![2](https://user-images.githubusercontent.com/93541353/139987236-498d1f50-78e8-4f3e-93bc-aedca161e013.PNG)
## Ý tưởng
* Muốn tính tổng các chữ số trong n thì cần phải tách các chữ số của n và tạo một biến s để tính tổng bằng các số đã tách
* Song song với tách số cần phải xóa chữ số cuối của n
## Code
```
#include <iostream>
using namespace std;

int main() {
	//tạo biến lưu trữ n và 1 biến lưu trữ tổng các chữ sô
	int n, s(0);
	//thực hiện nhập n, nếu n<0 thì nhập lại cho đến khi nào n>=0
	do {
		cout << "nhap n ";
		cin >> n;
	} while (n < 0);
	//nếu n vẫn còn số (n!=0) thì ta sẽ cộng vào s chữ số cuối của n, sau đó chia lấy dư để loại số đó ra
	while (n != 0) {
		s += n % 10;
		n /= 10;
	}
	//Xuất kết quả
	cout << "ket qua " << s;
	return 0;
}
```
# Bài 3
![3](https://user-images.githubusercontent.com/93541353/139987711-1f962068-e539-451a-b874-0da35d3cf310.PNG)
## Ý tưởng
* Ta thấy số hạng sau thứ i tử sẽ nhân thêm vào 1 lần x (x^i) và mẫu sẽ lại cộng thêm vào 1 số i. 
* Như vậy ta sẽ sử dụng vòng lặp để giải quyết bài toán này
## Code
```
#include <iostream>
using namespace std;

int main() {
	int n;
	double s(0), x, t(1), m(0);
	cout << "nhap n ";
	cin >> n;
	cout << "nhap x ";
	cin >> x;
	/*Cho i chạy từ 1 đến n, mỗi lần lặp thì t sẽ được nhân thêm x (có dạng x^i)
	mẫu sẽ được cộng thêm i (có dạng 1+2+...+i), s cộng thêm vào t/m*/
	for (int i = 1; i <= n; i++)
	{
		t *= x;
		m += i;
		s += t / m;
	}
	cout << "ket qua " << s;
	return 0;
}
```
# Bài 4
![4](https://user-images.githubusercontent.com/93541353/139993456-430421ea-6b1b-496b-923f-e24ce7566fed.PNG)
## Ý tưởng:
* Nhìn vào đề bai ta dễ dàng nhận ra các phần tử trong dãy tuân theo 1 quy luật nhất định
* Để dễ nhìn ta thử biến đổi phần tử tổng quát: (-1)^n*x^2n
					       =(-1)^n*(x^2)^n
					       =(-x^2)^n
* Như vậy ta chỉ cần sử dụng vòng lặp for chạy từ 1 đến n là giải quyết được bài toán
## Code: 
```
#include <iostream>
using namespace std;

int main() {
	int n;
	//p là 1 biến dùng để lưu giá trị của (-x*x)^i
	double x, s(0), p(1);
	cout << "nhap n ";
	cin >> n;
	cout << "nhap x ";
	cin >> x;
	/*Sau mỗi lần lập, p sẽ được nhân thêm -x*x, và cộng dồn kết quả cho s
	Ví dụ ở vòng lặp thứ 3, p=(-x*x)*(-x*x)*(-x*x)=-x^6 --> Đây là phần tử thứ 3 của dãy
	Sau đó ta lại lấy giá trị này cộng cho biến s*/
	for (int i = 1; i <= n; i++)
	{
		p *= -x * x;
		s += p;
	}
	cout << "ket qua " << s;
	return 0;
}
```
# Bài 5
![5](https://user-images.githubusercontent.com/93541353/139993578-6d520d5f-6d89-4a54-9cf6-9568355c6656.PNG)
## Ý tưởng
* Nhìn vào bài này ta sẽ cảm thấy nó có gì đó khó khăn 1 tí, nhưng thử theo 1 hướng nhìn khá khác bình thường 1 chút nào
* Với bài này ta thử nhìn từ x ra đến x^n ta sẽ thấy nó cũng chỉ là 1 vòng lặp chạy từ 1 đến n
* Để tính s thì ta sẽ sử dụng 1 biến để gán giá trị x^i, sau đó chỉ việc lấy căn của nó cộng với  s của i-1
## Code
```
#include <iostream>
using namespace std;

int main() {
	int n;
	double x, s(0), p(1);
	cout << "nhap n ";
	cin >> n;
	cout << "nhap x ";
	cin >> x;
	/*Ở đây, lấy ví dụ cho mọi người dễ hiểu thì i=1, 	p=x, 		s=sqrt(x)
						     i=2, 	p=x*x=x^2,	s=sqrt(x^2+sqrt(x)*/
	for (int i = 1; i <= n; i++)
	{
		p *= x;
		s = sqrt(p+s);
	}
	cout << "ket qua " << s;
	return 0;
}
```
# Bài 6
![6](https://user-images.githubusercontent.com/93541353/139993894-949e06e6-59e5-457a-814a-ee4e3c8bdd9c.PNG)
## Ý tưởng
* Theo em hiểu thì độ chính xác là 10^-6 thì số hạng cuối cùng của dãy phải >=10^-6, có nghĩa là 1/n>=10^-6
* Tuy nhiên thì em muốn sử dụng vòng lặp for cho bài toán này nên em cần tìm điều kiện dừng của vòng lặp
* Điều kiện để kết thúc là 1/n<10^-6, đồng nghĩa với việc i>10^5
## Code
```
#include <iostream>
using namespace std;

int main() {
	double s(0);
	//Tại đây khai báo kiểu dữ liệu của i là double vì i sẽ chứa 1 giá trị khá lớn
	for (double i = 1; i <= 10e5; i++)
		s += 1/i;
	cout << "ket qua " << s;
	return 0;
}
```
# Bài 7
![7](https://user-images.githubusercontent.com/93541353/139989835-026a87dc-4b15-4533-aae8-275bb94f8ddc.PNG)
## Ý tưởng
* Nhìn vào số hạng tổng quát ta nhận thấy phần tử phía sau có liên quan đến phía trước
* Đồng thời trong thành phần của phần tử còn có dạng mũ
* Ta sẽ sử dụng vòng lặp giải bài toán và cần có 2 biến khác để lưu giá trị của 3^i và 7^i
## Code
```
#include <iostream>
using namespace std;

int main() {
	//khi i=1 thì theo dề bài a=-2, b=3, c=7
	int a(-2), b(3), c(7), n;
	cout << "nhap n ";
	cin >> n;
	//Mỗi lần lập b sẽ được nhân thêm 3, c sẽ được nhân thêm 7 để có dạng b^i và 7^i
	for (int i = 2; i <= n; i++) {
		b *= 3;
		c *= 7;
		a = 5 * a + 2 * b - 6 * c + 12;
	}
	cout << "ket qua " << a;
	return 0;
}
```
# Bài 8
![8](https://user-images.githubusercontent.com/93541353/139989920-ee736b14-8c4a-4a64-9453-4cd869243d00.PNG)
## Ý tưởng
* Ở bài này em chỉ tìm 1 số tam giác đặc biệt như tam giác cân, tam giác đều, tam giác vuông và tam giác vuông cân
## Code
```
#include <iostream>
using namespace std;

int main() {
	int a, b, c;
	cout << "nhap 3 canh a, b, c: ";
	cin >> a >> b >> c;
	if ((a == b) || (a == c) || (b == c)) {
		if ((a * a + b * b == c * c) || (a * a + c * c == b * b) || (b * b + c * c == a * a))
			cout << "tam giac vuong can";
		else if ((a == b) && (b == c))
			cout << "tam giac deu";
		else cout << "tam giac can";
	}
	else if ((a * a + b * b == c * c) || (a * a + c * c == b * b) || (b * b + c * c == a * a))
		cout << "tam giac vuong";
	else cout<< "tam giac thuong";
	return 0;
}
```
# Bài 9
![9](https://user-images.githubusercontent.com/93541353/139990036-d9ed8dd6-7e49-4191-b2cb-314f8cdbe57f.PNG)
## Ý tưởng 
* Đây là 1 bài toán kiểm tra đúng sai nên thường em sẽ sử dụng biến bool để lưu trữ đáp án
* Điều kiện để số a là số chính phương là tồn tại 1 số tự nhiên sao cho số tự nhiên đó bình phương lên sẽ bằng a
* Để tìm số tự nhiên đó ta sẽ sử dụng vòng lặp for
## Code
```
#include <iostream>
using namespace std;

int main() {
	//Lúc đầu khởi tạo biến b lưu trức giá trị đúng sai và mặc định nó là sai.
	int n; bool b(0);
	cout << "nhap n ";
	cin >> n;
	//Cho i chạy đên khi nào i>sqrt(n) thì dừng lại
	//Trong quá trình đó nếu có tồn tại 1 số i nào bình phương lên=n thì giá trị của biến b sẽ nhảy lên 1(đúng)
	for (int i = 1; i * i <= n; i++)
		if (i * i == n)
			b = 1;
	//Kiểm tra lại biến b xem nó đang lưu trữ kết quả nào
	if (b == 1)
		cout << "day la so chinh phuong";
	else cout << "day khong la so chinh phuong";
	return 0;
}
```
# Bài 10
![10](https://user-images.githubusercontent.com/93541353/139990121-1a4f3ee4-5fe9-4f22-a7b3-8fc1e896dbb9.PNG)
## Ý tưởng 
* Cũng giống bài trên, vì đây là bài có tính kiểm tra đúng sai nên em sẽ sử dụng 1 biến bool để lưu kết quả
* Số có dạng 5^m=5*5*5...*5, Ví dụ: 5^1=5, 5^2=5*5, 5^3=5*5*5,...
* Từ đó ta thấy được bài này có thể xử lí được bằng vòng lặp, tuy nhiên lần này ta sẽ thay đổi 1 chút, sau mỗi lần lặp thì i*=5
## Code
```
#include <iostream>
using namespace std;

int main() {
	int n; bool b(0);
	cout << "nhap n ";
	cin >> n;
	for (int i = 1; i <= n; i *= 5)
		if (i == n) b = 1;
	if (b == 1)
		cout << "co";
	else cout << "khong";
	return 0;
}
```
