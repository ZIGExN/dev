### はじめに (Mở đầu)
この規約は参考URLの内容をもとに、田井の独断と偏見によって作成されております。
Quy ước này được tạo bởi quan điểm và độc đoán của Mr. Tai(田井)  dựa trên nội dung URL tham khảo. 

ご意見のある方はどんどんコメントをお寄せください。
Ai có ý kiến vui lòng để lại comment nhanh nhé.

#####  Tham khảo
http://shugo.net/ruby-codeconv/codeconv.html

## Ruby
### Indent (thụt đầu dòng)
- Sử dụng 2 space khi thụt đầu dòng
- CẤM không được sử dụng Tab 

### Indent khi sử dụng Case
Thụt đầu dòng của câu lệnh case

Phần `when ..else` trong câu lệnh `case` không cần thụt đầu dòng

Ví dụ:
```rb
case hoge
when 1
  ...
when 2
  ...
else
  ...
end
```

Không được như sau:
```rb
case hoge
  when 1
    ...
  when 2
    ...
  else
    ...
end
```

### Số ký tự trên mỗi dòng

Số ký tự của 1 dòng thì bao gồm luôn ký tự thụt đầu dòng thì tối đa là **100** ký tự

### Dòng trắng tiếp theo của dòng code cuối cùng
Không để dư dòng tiếp theo sau dòng code cuối.

Ví dụ:
```rb
class Hoge
  ...
end↵
```
Không được như sau:
```rb
class Hoge
 ...
end↵
↵
↵
↵
```

### Qui định về đưa 1 khoảng trắng (space)

- Sau mỗi toán tử (operator), sau đấu phẩy thì phải đưa vào 1 space trắng.
Ví dụ: `a = b + 1`

### Qui định về quote (đấu nháy)

Đối với String, việc sử dụng single quote ('), double quotes (") được qui định như sau:

* *Double quotes*: triển khai phương trình bên trong string, cú pháp Backslash, những string có chứa single quote
Ví dụ: 
```
print("My age is #{age}.")
print("My name is Giang. ¥n Hello!")
print("My name is #{'Giang'}.")
```


* *Single quote*: những string ngoài trường hợp trên

Hơn thế nữa, trong trường hợp String có chứa double quotes thì không được escape mà phải sử dụng `%Q{}`

Ví dụ
```rb
'string'
"abc#{hoge}def"
"abc\ndef"
"abc'd'ef"
%Q{abc"d"ed}
```
Không được như sau:
```rb
"string"
"abc\"d\"ef"
```

### Tên biến số

Tên biến số phải được đặt phải thể hiện được ý nghĩa tương đồng với nội dung nó chứa.

また全て英数字小文字とし単語の区切りは"\_"とする。(スネークケース)
Biến số thì toàn bộ phải được đặt bằng chữ thường và số, giữa các từ thì phân chia nhau bằng "\_"

ArrayやHashの場合は複数形にする。
Đối với trường hợp Array và Hash là dạng từ ở thể số nhiều.

基本的に単語を省略せずに使用する。
Về cơ bản là không được giản lược cụm từ.

Tuy nhiên, cũng có  trường hợp đối với những từ ý nghĩa đã rõ ràng chẳng hạn như là number ->num thì ok.
Trường  hợp scope nhỏ (khoảng xấp xỉ trong 5 dòng, chủ yếu là phạm vi mà có thể  nhìn thấy được) thì sơ lược đi cũng ok.

(Ví dụ)
```rb
area = Area.first
prefectures = Prefecture.all
num = 1
Sample.all.each do |s|
  (Trong 5 dòng)
end
```
Không nên
```rb
ar = Area.first
prefecture = Prefecture.all
Sample.all.each do |s|
  (Trên 5 dòng)
end
```

### Tên method

Phân chia các cụm từ chữ thường và số tiếng anh bằng "\_"

Nếu method trả về kiểu Boolean thì  thêm "?" vào cuối method chứ không đặt tên kiểu is\_xxx 

Trường hợp nếu method là dạng destructive thì nên thêm "!" vào cuối 

### Tên class/module 

Dùng CamelCase cho việc đặt tên Class. Không dùng "\_" để nối giữa các từ.
ただしHTTPなどのように、「先頭大文字、残り小文字」よりも通りがいい単語の場合はそちらを使用する。

### 定数名 (Tên hằng số)
全て大文字とし、単語の区切りは"\_"とする。
Tất cả các chữ cái, các từ vựng, ngăn cách bởi "\ _".

その他のルールは変数名に準拠する。
Các quy định khác thực hiện theo tên biến.

### Hashのキー (Key của Hash)
HashのキーはできるだけSymbolにし、可能な限りハッシュリテラル(key: value)で定義する。
	Đối với Key của Hash thì cố gắng chọn symbol, và cố hết sức định nghĩa bằng Hash literal (key: value)
	
ただし、Integerをキーにする場合などは従来(key => value)の方法で定義する。
Tuy nhiên, Với trường hợp chọn key là Integer chẳng hạn thì sẽ định nghĩa như cách thức từ trước đến giờ  (key => value). 

キーの命名規則は変数名の命名規則に準拠する。
Còn với quy tắc đặt tên key thì sẽ căn cứ theo rule đặt tên của tên biến số.

キーにSymbolとIntegerが混在する場合は従来の方法で統一して定義する。
Trường hợp Symbol và Integer trộn lẫn trong Key thì sẽ thống nhất theo cách thức từ trước đến giờ để định nghĩa.

例外として、大文字であったりStringであったほうが都合が良い場合
(たとえばPOST時にクライアントの応募フォームのname属性に合わせた場合や、
 DBのvarcharにキーを合わせた場合 など)はこの限りではない。
Ví dụ: Trong tường hợp là chữ hoa và là String mới phù hợp ( ví dụ:trường hợp làm cho phù hợp với thuộc tính name của  application form của client khi POST, và trường hợp điều chỉnh cho key phù hợp với varchar của DB ,v v..) thì sẽ không áp dụng điều này.
	
	
例：(Ví dụ)
```rb
hoge = {key1: value1, key2: value2}
fuga = {1 => value1, 2 => value2}
bar  = {1 => value1, :key2 => value2}
```
ダメ：(Không nên)
```rb
hoge = {'key1' => value1, 'key2' => value2}
fuga = {:key1 => value1, :key2 => value2}
bar  = {1 => value1, key2: value2}
```

StringキーがOKなパターン：
```rb
area_numbers = {'kanto' => 1, 'kansai' => 2}
area = Area.find_by_code('kanto')
puts area_numbers[area.code]
```

### requireの記述箇所 (Nơi bổ sung require)
requireはファイルの先頭で行う。
require thì nên tổ chức ở trên cùng của file

class宣言後やメソッド内では行わない。
không nên thực hiện sau class hoặc trong method.

例： (Ví dụ)
```rb
require 'hoge'
require 'fuga'

class Bar
  ...
end
```
ダメ： (Không nên)
```rb
class Bar
  require 'hoge'

  def sample
    require 'fuga'
    ...
  end
end
```

### アクセサの定義 (Định nghĩa accessor)
アクセサの定義には、attr_accessor・attr_reader・ attr_writerを使用する。(attrは使用しない。)
accessor  thì sử dụng attr_accessor・attr_reader・ attr_writer( không sử dụng attr)

### メソッドの定義 (Định nghĩa method)
メソッド定義の仮引数リストには括弧を付ける。 ただし、引数がない場合は、括弧を省略する。
Danh sách các parameter của method thì thêm dấu ngoặc.Tuy nhiên,trường hợp không có biến số thì có thể giản lược

また"("の前後、")"の前にスペースを空けない。
Lại nữa,không để space trống trước "(" và sau ")"

例：(Ví dụ)
```rb
def foo(x, y)
  ...
end

def foo
  ...
end
```
ダメ：(Không nên)
```rb
def foo x, y
  ...
end

def foo()
  ...
end

def foo ( x, y )
 ...
end

```

### クラスメソッドの定義 (Định nghĩa class method)
クラスメソッドの定義にはselfを使用する
Class method thì hãy sử dụng self.

例：(Ví dụ)
```rb
class Hoge

  def self.fuga
    ...
  end

  または (Hoặc là)

  class << self

    def fuga
      ...
    end

  end

end
```
ダメ： (Không nên)
```rb
class Hoge

  def Hoge.fuga
    ...
  end

end
```

### クラス内でのインスタンスメソッドの呼び出し (Call Instance trong một class)
クラス内でインスタンスメソッドを呼び出す時はself.を付ける。
Khi gọi instance trong class thì xin hãy thêm vào "self."

ローカル変数との混同を避けるため。
Để tránh nhầm lẫn với các biến local.

例：(Ví dụ)
```rb
class Hoge

  has_one :aba

  def fuga
    ...
  end

  def bar
    self.fuga
    self.aba
    ...
  end

end
```

### メソッドの呼び出し (Call method)
基本的にメソッドを呼び出しの引数リストには、

* 引数なし → 括弧を省略 
   không có biến số →  giản lược(bỏ) dấu ngoặc
			
* 引数あり → 括弧を付ける
   có biến số →  thêm dấu ngoặc

以下のものは省略してもよい。
Những cái được ghi dưới đây giản lược cũng tốt
* print
* puts
* p
* return

以下のものは必ず省略する。
Những cái dưới đây chắn chắn phải bỏ
* require
* include
* extend
* validateやhas_oneなどフィルタ的に実行するメソッド

例：(Ví dụ)
```rb
require 'csv'

class Hoge

  include Module1
  extend  Module2

  has_one :fuga

  def sample
    puts 'abc'

    time = Time.zone.now.strftime('%Y-%m-%d')

    return time
  end

end
```

### ブロック (block)
ブロックは基本的に do ... end を使用する
Block thì cơ bản sử dụng do...end

メソッドチェインをする場合は { ... } を使用する
Trường hợp check in method thì sử dụng  { ... }

また、{ ... } を使用する際はメソッドとの間・ブロック引数の間はスペースをあけ、
Hơn nữa khi sử dụng  { ... } thì khoản cách giữa các biến số block ・ khoản cách giữa các method thì thêm space

1行の場合は最後の処理と } の間にスペースをあける。
trường hợp 1 dòng thì thêm space vào } của xử lý cuối dùng.

例：(Ví dụ)
```rb
hoges.each do |hoge|
  ...
end

hoges.map { |hoge| hoge.fuga }.join
hoges.map { |hoge|
  hoge.fuga
}.join
```
ダメ：(Không nên)
```rb
hoges.each {|hoge|
  ...
}

hoges.map{|hoge| hoge.fuga}
hoges.map do |hoge| hoge.fuga end.join
```

### 論理演算子 (Toán tử luận lý)
論理演算には!や&&や||を使用する。 (not/and/orは使用しない。)
Trong toán tử luận lý sử dung ! hay && hay || .(not/and/or thi không nên sử dụng)

### if / unless
* 括弧・then は省略する。
   giản lược dấu ngoặc・then
			
* 否定のifはunlessを使用する(if !x -> unless x)
  phủ định if thì nên dùng unless 
		
* だだし、複数条件のunlessは逆にifに置き換える
  Tuy nhiên, với nhiều điều kiện thì có thể hoán đổi unless bằng if.
		
* unlessではelseは使用しない
  Trong unless không dùng else.
		
* 条件が簡単で1行で書ける場合のみ修飾子は使用してもよい
 Chỉ trường hợp điều kiện đơn giản và có thể viết trong 1 dòng, thì sử dụng từ bổ nghĩa(modifier) cũng được.
		
* 複数行ブロックに修飾子は使用しない
   modifier trong block nhiều dòng thì không sử dụng.
			
例：(Ví dụ)
```rb
if hoge
  ...
end

if !x && y
  ...
end

unless x
  ...
end

x = 1 if bar.present?
y = 1 unless bar.blank?
```
ダメ：(Không nên)
```rb
if(hoge)
  ...
end

if hoge then
  ...
end

if !x
  ...
end

unless x || !y
  ...
else
  ...
end

x = 1 if bar >= y && fuga <= z

hoges.each do |hoge|
  ...
end if bar.present?
```

### return
メソッドの値を返す場合は、必ずreturnを使用する。 また、returnの括弧は省略する。
Trường hợp trả về trị trong method thì chắn chắn phải dùng return.Hơn nữa cũng có thể giản lược dấu () trong return.

例： (Ví dụ)
```rb
def add(x, y)
  return x + y
end
```
ダメ：(Không nên)
```rb
def add(x, y)
  x + y
end

def add(x, y)
  return(x + y)
end
```

### 繰り返し (Vòng lặp)

whileのdoは省略する。また、while !xのような場合は、 until xに置き換える。
vòng lặp do while thì không dùng. Hơn nữa, trường hợp giống như while !x thì có thể hoán đổi bằng until x.

例：(Ví dụ)
```rb
while cond
  ...
end

until cond
  ...
end
```
ダメ： (Không nên)
```rb
while cond do
  ...
end
```

また、無限ループにはloopを使用する。(Hơn nữa với vòng lặp vô hạn có thể sử dụng loop)

例：(Ví dụ)
```rb
loop do
  ...
end
```
ダメ：(Không nên)
```rb
while true
  ...
end
```

for ... in のループは使用しない。
loop trong for ... in thì không sử dụng

forはループの内外でスコープが変わらないため、
for thì vì  không biến đổi phạm vi  bên trong trong vòng lặp.

ループ外部に予期せぬ影響をあたえる可能性があるため。
Vì có  khả năng gây ra những ảnh hưởng không mong đợi bên ngoài vòng lặp.

### 三項演算子 (toán tử với 3 mục)
明らかに可読性に問題がない場合を除いて、三項演算子はなるべく使用しない。
とくに、括弧が必要なほど条件が複雑な場合や、複数行になってしまう 場合は、三項演算子は使用しない。
Đặc biệt nếu điều kiện phức tạp hay nhiều dòng thì không sử dụng toán tử này.
	
### 条件分岐によりtrue / falseを設定する場合 (Trường hợp  set là true / flase theo phân chia điều kiện)
true / false を返す結果によってtrue / false を設定するのは無駄なので、条件文をそのまま変数にいれる。
 Việc set true / false tùy vào kết quả trả về true / false thì vì không cần thiết, cứ để biến số như vậy trong câu điều kiện .
	
例：(Ví dụ)
```rb
flag = a < b
```
ダメ：(Không nên)
```rb
flag = true if a < b
flag = a < b ? true : false
```

## Rails

### Rails project guidelines
File .gitignore mẫu khi add vào Git Repository như sau.
```
# Ignore bundler config.
/.bundle

# Ignore all logfiles and tempfiles.
.rspec
/log
/tmp
/db/*.sqlite3
/db/*.sqlite3-journal
/public/system
/vendor/bundle
.ruby-gemset
```

Những phần không được thêm vào .gitignore
```
Gemfile.lock
.ruby-version
```

### グローバル変数 (biến global)
グローバル変数($から始まる変数)は原則として使用禁止。
biến global(bắt đầu với $) thì theo nguyên tắc thì cấm sử dụng.

### ActiveRecordのcondition
whereに与えるconditionは、1条件の場合は積極的にarelを使用する。
Điều kiện được đưa vào trong where nếu có 1 điều kiện thì sử dụng arel.

arelの方が圧倒的にパフォーマンスが良いため。
theo hướng areal thì performance sẽ tốt hơn.

逆に、2つ以上の条件がある場合はarelは可読性が著しく悪いため、"?"埋め込みや、Hashでのconditionにする。
Ngược lai, nếu từ 2 điều kiện trở lên nếu areal thì khả năng read sẽ khá tệ cho nên trong condition nên là Hash hay là chèn thêm "?"

また、式展開でのconditionはインジェクションの危険性を孕むため、**絶対に使用禁止**。
Hơn nữa ,condition trong phương thức tự phát triển thì sẽ có injection có tính nguy hiểm  **tuyệt đối cấm sử dụng**.

例：(Ví dụ)
```rb
hoges = Hoge.where(Hoge.arel_table[:column].match('a%'))
hoges = Hoge.where('column1 = 1 OR column2 = ?', column_value)
hoges = Hoge.where(column1: 1, column2: column_value)
```
ダメ： (Không nên)
```rb
hoges = Hoge.where(Hoge.arel_table[:column1].eq(1).or(Hoge.arel_table[:column2].eq(column_vlaue)))
hoges = Hoge.where("column1 = 1 OR column2 = #{column_value}")
```

### ActiveRecord#count
ActiveRecordのcountメソッドを使用して単純なレコード数を数える場合はPRIMARY KEYのselectとセットで使う。
Nếu đếm số record đơn sử dụng method count của ActiveRecord thì sử dụng bằng cách set và select PRIMARY KEY

例： (Ví dụ)
```rb
Hoge.select(:id).count
```

### 有無を調べる場合 (Trường hợp tìm yesno)
有無を調べる場合はblank?・present?を明示的に付ける。
Với trường hợp này để rõ ràng nên thêm blank? hay là present? 

例： (Ví dụ)
```rb
if hoge.blank?
  ...
end

if hoge.present?
  ...
end
```
ダメ：(Không nên)
```rb
unless hoge
  ...
end

if hoge
  ...
end
```

### erbタグ (erb tag)
erbタグ(<% %>)は出力を伴わない場合は原則として開始・終了ともに"-"を付ける。
erb tag(<% %>) nếu không xuất thì theo nguyên tắc thêm "-" lúc bắt đầu và kết thúc

出力を伴う・伴わない、"-"を付ける・付けないにかかわらず、erbの開始タグ後と終了タグ前にはスペースを入れる。
bất kể thêm hay không thêm "-" ,không xuất hay xuất thì  trước tag bắt đầu và kết thúc erb hãy đưa vào space.

例：(Ví dụ)
```erb
<%-
  hoge = 1
-%>
<%- fuga = 'aaa' -%>
<%= bar %>
<%- fugas.each do |fuga| -%>
  ...
<%- end -%>
```
ダメ： (Không nên)
```erb
<%
  hoge = 1
%>
<% fuga = 'aaa' %>
<%=bar%>
<%-fugas.each do |fuga|-%>
  ...
<%-end-%>
```

### erbのインデント (Thụt đầu dòng của erb )
erbタグ内のインデントは初段で1つ下げる。  
indent trong erb tag thì hạ xuống 1 cấp. 

またerbタグそのもののインデントは出力されるHTMLに合わせる。
Hơn nữa những cái indent trong erbtag thì cũng có trong HTML được xuất ra.

例：(Ví dụ)
```erb
<%-
  hoge = 1
-%>

<div>
  <%- fugas.each do |fuga| -%>
  <%= fuga %>
  <%- end -%>
</div>
```

ダメ：(Không nên)
```erb
<%-
hoge = 1
-%>

<div>
  <%- fugas.each do |fuga| -%>
    <%= fuga %>
  <%- end -%>
</div>
```

### migration
timestamp型のカラムを定義する場合は、PRIMARY KEYの直後に定義する。
Nếu định nghĩa coloumn với hình thức  timestamp thì định nghĩa luôn sau trị PRIMARY KEY.

### rake task
rake taskを定義する場合はnamespece第1層にプロジェクト名を付ける。  
Nếu định nghĩa rake task,thì thêm tên project vào layer đầu của namespace

### rakeのファイル分割 (phân chia file của rake)
lib/tasksをルートとし、
project:taskname の場合は project.rakeに記述。
nếu là project:taskname thì bổ sung  project.rake

project:sub:taskname の場合は、project/sub.rakeに記述する。
nếu là project:sub:taskname thì bổ sung project/sub.rake

### URLの記述 (bổ sung URL)
サイト内のURLは、可能な限りnamed_path、named_urlを使用する。
URL trong site thì  sử dụng named_path、named_url thì càng tốt.

URLのベタ書きは原則として禁止。
Việc ghi header URL theo nguyên tắc bị cấm.

### form_tagとform_forの使い分け (Phân chia sử dụng form_tagとform_for)
ActiveRecordやActiveModelのオブジェクトを扱う場合のみform_forを使用し、
それ以外ではform_tagを使用する。  
Nếu xử lý object của ActiveRecord hay ActiveModel thì dùng form_for. Ngoài những cái đó thì dùng form_tag.

### フォームヘルパメソッドの使い分け (Phân chia sử dụng phương thức help)
text_fieldとtext_field_tag、check_boxとcheck_box_tag等の使い分けは、form_tag・form_forの使い分けと同様で、
Phân chia sử dụng text_fieldとtext_field_tag、check_boxとcheck_box_tag đồng nghĩa với việc phân chia cách sử dụng form_tag・form_for

ActiveRecordやActiveModelのオブジェクトを扱う場合のみ_tag無し版を使い、それ以外では_tagあり版を使う。
Sử dụng phiên bản không _tag với trường hợp Object của ActiveRecord , ActiveModel.Ngoài những cái đó sử dụng phiên bản có _tag

### paramsの書き換えについて (Về ghi đè params)
原則的にparamsの内容は上書きしない。
Trong nguyên tắc thì nội dung params thì không đươc ghi ở trên.

どうしても書き換える場合は別変数に入れる、もともとのparamsを退避させる、などすること。
Trường hợp thực hiện ghi đè thì bằng mọi cách phải cho lưu params gốc (ban đầu) và đưa vào biến số khác
