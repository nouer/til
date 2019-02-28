# moment.js
## moment生成
  - 現在時刻  
    `const now = moment();`

  - 文字列  
    `const date = moment('1999-01-31');`  
    ISO8601, RFC 2822がサポートされる
<pre>
    --- ISO8601 ---

    2013-02-08  # A calendar date part
    2013-W06-5  # A week date part
    2013-039    # An ordinal date part
    
    20130208    # Basic (short) full date
    2013W065    # Basic (short) week, weekday
    2013W06     # Basic (short) week only
    2013050     # Basic (short) ordinal date

    2013-02-08T09            # An hour time part separated by a T
    2013-02-08 09            # An hour time part separated by a space
    2013-02-08 09:30         # An hour and minute time part
    2013-02-08 09:30:26      # An hour, minute, and second time part
    2013-02-08 09:30:26.123  # An hour, minute, second, and millisecond time part
    2013-02-08 24:00:00.000  # hour 24, minute, second, millisecond equal 0 means next day at midnight
    
    20130208T080910,123      # Short date and time up to ms, separated by comma
    20130208T080910.123      # Short date and time up to ms
    20130208T080910          # Short date and time up to seconds
    20130208T0809            # Short date and time up to minutes
    20130208T08              # Short date and time, hours only

    2013-02-08 09  # A calendar date part and hour time part
    2013-W06-5 09  # A week date part and hour time part
    2013-039 09    # An ordinal date part and hour time part

    2013-02-08 09+07:00            # +-HH:mm
    2013-02-08 09-0100             # +-HHmm
    2013-02-08 09Z                 # Z
    2013-02-08 09:30:26.123+07:00  # +-HH:mm
    2013-02-08 09:30:26.123+07     # +-HH

    --- RFC 2822 ---

    6 Mar 17 21:22 UT
    6 Mar 17 21:22:23 UT
    6 Mar 2017 21:22:23 GMT
    06 Mar 2017 21:22:23 Z
    Mon 06 Mar 2017 21:22:23 z
    Mon, 06 Mar 2017 21:22:23 +0000
</pre>
  - 文字列＋フォーマット  
    `const date = moment("12-25-1995", ["MM-DD-YYYY", "YYYY-MM-DD"]);`

  - Unix Timestamp (milliseconds)   
    `const date =  moment(1318781876406);`

  - Unix Timestamp (seconds)   
    `const date = moment.unix(1318781876);`

  - Date Object  
    `const date = new Date(2011, 9, 16);`  
    `const dayWrapper = moment(date);`

  - Array  
    `cont date = moment([2010, 1, 14, 15, 25, 50, 125]); // February 14th, 3:25:50.125 PM`

  - cloneメソッド  
    `const date1 = moment();`
    `const date2 = date1.clone();`

  - UTC  
    `moment().format();     // 2013-02-04T10:35:24-08:00`
    `moment.utc().format(); // 2013-02-04T18:35:24+00:00`

  - parseZone  
    `moment.parseZone("2013-01-01T00:00:00-13:00").utcOffset(); // -780 ("-13:00" in total minutes)`  
    `moment.parseZone('2013 01 01 05 -13:00', 'YYYY MM DD HH ZZ').utcOffset(); // -780  ("-13:00" in total minutes)`  
    `moment.parseZone('2013-01-01-13:00', ['DD MM YYYY ZZ', 'YYYY MM DD ZZ']).utcOffset(); // -780  ("-13:00" in total minutes);`

## Get Set
  - Millisecond
<pre>
moment().millisecond(Number);
moment().millisecond(); // Number
moment().milliseconds(Number);
moment().milliseconds(); // Number
</pre>

  - Second
<pre>
moment().second(Number);
moment().second(); // Number
moment().seconds(Number);
moment().seconds(); // Number
</pre>

  - Minute
<pre>
moment().minute(Number);
moment().minute(); // Number
moment().minutes(Number);
moment().minutes(); // Number
</pre>

  - Hour
<pre>
moment().hour(Number);
moment().hour(); // Number
moment().hours(Number);
moment().hours(); // Number
</pre>

  - Date of Month
<pre>
moment().date(Number);
moment().date(); // Number
moment().dates(Number);
moment().dates(); // Number
</pre>

  - Day of Week
<pre>
moment().day(Number|String);
moment().day(); // Number
moment().days(Number|String);
moment().days(); // Number
</pre>

  - Day of Week(Locale Aware)
<pre>
moment().weekday(Number);
moment().weekday(); // Number
</pre>

  - ISO Day of Week
<pre>
moment().isoWeekday(Number);
moment().isoWeekday(); // Number
</pre>

  - Day of Year
<pre>
moment().dayOfYear(Number);
moment().dayOfYear(); // Number
</pre>

  - Week of Year
<pre>
moment().week(Number);
moment().week(); // Number
moment().weeks(Number);
moment().weeks(); // Number
</pre>

  - Week of Year(ISO)
<pre>
moment().isoWeek(Number);
moment().isoWeek(); // Number
moment().isoWeeks(Number);
moment().isoWeeks(); // Number
</pre>

  - Month
<pre>
moment().month(Number|String);
moment().month(); // Number
moment().months(Number|String);
moment().months(); // Number
</pre>

  - Quarter
<pre>
moment().quarter(); // Number
moment().quarter(Number);
moment().quarters(); // Number
moment().quarters(Number);
</pre>

  - Year
<pre>
moment().year(Number);
moment().year(); // Number
moment().years(Number);
moment().years(); // Number
</pre>

  - Week Year
<pre>
moment().weekYear(Number);
moment().weekYear(); // Number
</pre>

  - Week Year(ISO)
<pre>
moment().isoWeekYear(Number);
moment().isoWeekYear(); // Number
</pre>

  - Weeks in Year
<pre>
moment().weeksInYear();
</pre>

  - Weeks in Year(ISO)
<pre>
moment().isoWeeksInYear();
</pre>

  - Get
<pre>
moment().get('year');
moment().get('month');  // 0 to 11
moment().get('date');
moment().get('hour');
moment().get('minute');
moment().get('second');
moment().get('millisecond');
</pre>

  - Set
<pre>
moment().set(String, Int);
moment().set(Object(String, Int));
</pre>

  - Maximum
<pre>
moment.max(Moment[,Moment...]);
moment.max(Moment[]);
</pre>

  - Minimum
<pre>
moment.min(Moment[,Moment...]);
moment.min(Moment[]);
</pre>

## 操作
  - Add
<pre>
</pre>

  - Subtract
<pre>
</pre>

  - Stat of Time
<pre>
</pre>

  - End of Time
<pre>
</pre>

  - Maximum
<pre>
</pre>

  - Minimum
<pre>
</pre>

  - Local
<pre>
</pre>

  - UTC
<pre>
</pre>

  - UTC offset
<pre>
</pre>

  - Time zone Offset
<pre>
</pre>


## 表示
  - Format
<pre>
</pre>

  - Time from now
<pre>
</pre>

  - Time from X
<pre>
</pre>

  - Time to now
<pre>
</pre>

  - Time to X
<pre>
</pre>

  - Calender Time
<pre>
</pre>

  - Difference
<pre>
</pre>

  - Unix Timestamp(milliseconds)
<pre>
</pre>

  - Unix Timestamp(seconds)
<pre>
</pre>

  - Days in Month
<pre>
</pre>

  - As Date Object
<pre>
</pre>

  - As Array
<pre>
</pre>

  - As JSON
<pre>
</pre>

  - As ISO8601 String
<pre>
</pre>

  - As Object
<pre>
</pre>

  - As String
<pre>
</pre>

  - Inspect
<pre>
</pre>


## 判定
  - Is Before
<pre>
</pre>

  - Is Same
<pre>
</pre>

  - Is After
<pre>
</pre>

  - Is Same or Before
<pre>
</pre>

  - Is Same or After
<pre>
</pre>

  - Is Between
<pre>
</pre>

  - Is Daylight Saving Time
<pre>
</pre>

  - Is DST Sfifted
<pre>
</pre>

  - Is Leap Year
<pre>
</pre>

  - Is a moment
<pre>
</pre>

  - Is a Date
<pre>
</pre>


