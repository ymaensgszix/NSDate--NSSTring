# NSDate--NSSTring
代码片段
//获取系统当前时间
NSDate *currentDate = [NSDate date];
//用于格式化NSDate对象
NSDateFormatter *dateFormatter = [[NSDateFormatter alloc] init];
//设置格式：zzz表示时区
[dateFormatter setDateFormat:@"yyyy-MM-dd HH:mm:ss zzz"];
//NSDate转NSString
NSString *currentDateString = [dateFormatter stringFromDate:currentDate];
//输出currentDateString
NSLog(@"%@",currentDateString);
NSDateFormatter常用的格式有：

yyyy-MM-dd HH:mm:ss.SSS 
yyyy-MM-dd HH:mm:ss
yyyy-MM-dd
MM dd yyyy
NSDateFormatter格式化参数如下：

G: 公元时代，例如AD公元
yy: 年的后2位
yyyy: 完整年
MM: 月，显示为1-12
MMM: 月，显示为英文月份简写,如 Jan
MMMM: 月，显示为英文月份全称，如 Janualy
dd: 日，2位数表示，如02
d: 日，1-2位显示，如 2
EEE: 简写星期几，如Sun
EEEE: 全写星期几，如Sunday
aa: 上下午，AM/PM
H: 时，24小时制，0-23
K：时，12小时制，0-11
m: 分，1-2位
mm: 分，2位
s: 秒，1-2位
ss: 秒，2位
S: 毫秒
NSString转NSDate

既然NSDate可以转成NSString，毫无疑问NSString也可以转成NSDate。代码如下：

//需要转换的字符串
NSString *dateString = @"2015-06-26 08:08:08";
 //设置转换格式
NSDateFormatter *formatter = [[NSDateFormatter alloc] init] ;
[formatter setDateFormat:@"yyyy-MM-dd HH:mm:ss"];
//NSString转NSDate
NSDate *date=[formatter dateFromString:dateString];
NSDate和NSString相互转换就是这么简单。

转换工具类

在项目中，我们需要用到转换的地方可能不止一处，所以建议我们定义一个工具类。在工具类里实现如下两个方法：

//NSDate转NSString
+ (NSString *)stringFromDate:(NSDate *)date
{
    //获取系统当前时间
    NSDate *currentDate = [NSDate date];
    //用于格式化NSDate对象
    NSDateFormatter *dateFormatter = [[NSDateFormatter alloc] init];
    //设置格式：zzz表示时区
    [dateFormatter setDateFormat:@"yyyy-MM-dd HH:mm:ss zzz"];
    //NSDate转NSString
    NSString *currentDateString = [dateFormatter stringFromDate:currentDate];
    //输出currentDateString
    NSLog(@"%@",currentDateString);
    return currentDateString;
}

//NSString转NSDate
+ (NSDate *)dateFromString:(NSString *)string
{
    //需要转换的字符串
    NSString *dateString = @"2015-06-26 08:08:08";
    //设置转换格式
    NSDateFormatter *formatter = [[NSDateFormatter alloc] init] ;
    [formatter setDateFormat:@"yyyy-MM-dd HH:mm:ss"];
    //NSString转NSDate
    NSDate *date=[formatter dateFromString:dateString];
    return date;
}
