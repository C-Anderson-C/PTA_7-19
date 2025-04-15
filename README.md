# PTA_7-19
# 支票面额
# 一个采购员去银行兑换一张y元f分的支票，结果出纳员错给了f元y分。采购员用去了n分之后才发觉有错，于是清点了余额尚有2y元2f分，问该支票面额是多少？

# 输入格式：输入在一行中给出小于100的正整数n。

# 输出格式：在一行中按格式y.f输出该支票的原始面额。如果无解，则输出No Solution。
```cpp
#include <iostream>
#include <iomanip>

using namespace std;

int main() {
	int n;
	cin >> n;
	bool found = false;

	for (int y = 0;y < 100;++y) {
		for (int f = 0;f < 100;++f) {
			int original = 100 * f + y;
			int wrong = 100 * f + y;
			int remain = 200 * y + 2 * f;

			if (wrong - n ==remain ) {
				cout << y<<"." << f << endl;  //千万不要多去把他转换成小数，不然必错
				found = true;
				break;
			}
		}
		if (found) {
			break;
		}
	}
	if (!found) {
		cout << "No Solution" << endl;
	}
	return 0;
}