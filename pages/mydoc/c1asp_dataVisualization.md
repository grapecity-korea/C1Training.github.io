---
title: ComponentOne for ASP.NET | 데이터 분석 & 시각화
keywords: ComponentOne, ASP.NET, 웹폼, 데이터 분석, 시각화, data analysis, data visualization
last_updated: Aug 08, 2019
summary: "ComponentOne for ASP.NET 이 제공하는 데이터 분석 및 시각화 컨트롤을 소개합니다."
sidebar: mydoc_sidebar
permalink: c1asp_dataVisualization.html
folder: mydoc
---


## C1LineChart 사용자 정의의 선형차트만들기

ASP.NET 의 C1LineChart는 라인 차트, 영역 차트 및 스플라인 차트를 통합했습니다. 라인차트는 각 시리즈를 데이터의 연결지점으로 가져오고, 풍부한 커스터마이즈 옵션과 애니메이션을 포함합니다.  
본문에서는 C1LineChart로 어떻게 사용자 정의의 선형차트를 만드는지 소개합니다. 첨부 Demo의 코드는 차트에서 제목을 추가하는 방법, 축 서식을 지정하는 방법, 차트 레이블을 추가하는 방법 및 차트의 데이터를 계산하는 방법을 보여줍니다.  
구체적인 방법은 다음과 같습니다.

  

### C1LineChart컨트롤을 web프로그램에 추가

C1LineChart 설정

C1LineChart.Header.Text를 통해 타이틀을 추가합니다. C1LineChart. ShowChartLabels 의 속성을 통해 차트 레이블의 표시여부를 설정합니다. ChartLabelStyledml 속성으로 레이블의 스타일을 설정합니다. C1LineChart.Axis를 통해 텍스트 형식, 표시 위치, 텍스트 스타일 등을 포함하여, X, Y축의 정보를 설정합니다. C1LineChart.Hint를 통해 애니메이션 효과, 표시 방법, 딜레이 등을 통해 어떻게 툴팁을 표시할지 여부를 설정합니다. C1LineChart.Aimation를 통해 애니메이션 및 애니메이션 딜레이 등의 표시방법을 설정합니다.

구체적인 코드는 다음과 같습니다：

  

```csharp
<wijmo:C1LineChart runat="server" ID="C1LineChart1" ShowChartLabels="False" Height="475" Width="756">
    <Animation Duration="2000"></Animation>
    <Header Text="온라인사용자">
    </Header> 
    <Footer Compass="South" Visible="False"> 
    </Footer>
    <Legend Visible="false">
    </Legend>
    <Hint OffsetY="-10">
        <Content Function="hintContent" />
    </Hint> 
</wijmo:C1LineChart>
```

### C1LineChart시리즈 설정

[C1 Line Chart 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1LineChart-overview.zip)

페이지가로드되면 코드로 C1LineChart 패밀리를 추가하고 LineChartSeries를 작성한 다음 C1LineChart.SeriesList.Add를 통해 이를 추가합니다. 계열의 다양한 속성을 설정할 수 있습니다. 예를 들어 일련의 태그 유형, 레이블 시리즈 등을 설정할 수 있습니다. 위의 기능을 수행하려면 PageLoad 이벤트에서 다음 코드를 호출하십시오.

```csharp
//Invoke in Page Load event
private void PrepareOptions()
{
    var valuesX = new List(){new DateTime(2010, 10, 27, 11, 48, 0), new DateTime(2010, 10, 27, 13, 47, 0), new DateTime(2010, 10, 27, 15, 46, 0), new DateTime(2010, 10, 27, 17, 45, 0), 
    new DateTime(2010, 10, 27, 19, 44, 0), new DateTime(2010, 10, 27, 21, 43, 0), new DateTime(2010, 10, 27, 23, 41, 0), new DateTime(2010, 10, 28, 1, 40, 0), new DateTime(2010, 10, 28, 3, 39, 0), 
    new DateTime(2010, 10, 28, 5, 38, 0), new DateTime(2010, 10, 28, 7, 37, 0), new DateTime(2010, 10, 28, 9, 36, 0), new DateTime(2010, 10, 28, 11, 35, 0), new DateTime(2010, 10, 28, 13, 34, 0), 
    new DateTime(2010, 10, 28, 15, 33, 0), new DateTime(2010, 10, 28, 17, 32, 0), new DateTime(2010, 10, 28, 19, 31, 0), new DateTime(2010, 10, 28, 21, 30, 0), new DateTime(2010, 10, 28, 23, 38, 0), 
    new DateTime(2010, 10, 29, 1, 27, 0), new DateTime(2010, 10, 29, 3, 26, 0), new DateTime(2010, 10, 29, 5, 25, 0), new DateTime(2010, 10, 29, 7, 24, 0), new DateTime(2010, 10, 29, 9, 23, 0), new DateTime(2010, 10, 29, 11, 22, 0)};
    var valuesY = new List() { 2665513, 2300921, 1663229, 1622528, 1472847, 1354026, 1348909, 1514946, 1746392, 2020481, 2312976, 2539210, 2657505, 2369938, 1869805, 1648695, 1529983, 1398148, 1389668, 1568134, 1787466, 2101460, 2090771, 2351994, 2537400 };

    //serieslist
    var series = new LineChartSeries();
    this.C1LineChart1.SeriesList.Add(series);
    series.Markers.Visible = true;
    series.Markers.Type = MarkerType.Circle;
    series.Data.X.AddRange(valuesX.ToArray());
    series.Data.Y.AddRange(valuesY.ToArray());
    series.Label = "Users";
    series.LegendEntry = true;
}
```

위의 방법을 통해 본문에 첨부한 Demo와 같이 C1LineChart를 구현할 수 있습니다. 실행 결과는 다음과 같습니다.

![](https://www.grapecity.co.kr/images/training/c1/tc4-1-1.png)

  

페이지가 로드 되고, 마우스를 데이터의 포인트 위에 올리면 애니메이션 효과와 함께 툴팁 메시지가 나타납니다.

본문 demo소스 코드는 다음과 같습니다. :

[C1 Line Chart 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1LineChart-overview.zip)


## C1BarChart데이터 소스를 통한 막대그래프의 생성

C1BarChart는 사용빈도가 가장 높은 컨트롤 중 하나입니다. 본문에서는 데이터소스를 바탕으로 어떻게 막대 그래프를 작성하는지 소개합니다. Demo예시의 코드는 어떻게 X축과 Y축 텍스트를 설정하는지, 그래프 머리글을 어떻게 추가하는지, 태그 문자를 어떻게 추가하는지 및 데이터로 그래프를 어떻게 채우는지 소개합니다.

C1BarChart데이터 소스를 통해 막대그래프를 생성하는 방법은 다음과 같습니다.

  

먼저 C1BartChart컨트롤을 web응용프로그램에 추가합니다.

### X축과 Y축의 텍스트 설정

C1BarChart的Axis태그를 통해 X, Y축의 텍스트를 설정합니다. Axis.X.Text와 Axis.Y.Text에 각각 X축과 Y축의 텍스트를 설정합니다. 코드는 다음과 같습니다.

  

```csharp
<Axis>
    <X Text=""></X>
    <Y Text="전체 하드웨어" Compass="West"></Y>
</Axis>
```

### 태그 텍스트 추가

C1BarChart의 레이블은 ShowChartLabels를 통해 표시됩니다. ChartLabelFormatString는 레이블의 형식을 설정합니다. ChartLabelStyle는 레이블의 스타일을 표시합니다.

  

### 데이터로 그래프 채우기

[C1 Bar Chart 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1BarChart-Overview.zip)

C1BarChart의 SeriesList를 통해 BarChartSeries를 만들고,  태그로 X축, Y축의 값을 설정합니다. 코드는 다음과 같습니다.

```csharp
<SeriesList> 
    <wijmo:BarChartSeries Label="서부" LegendEntry="true"> 
        <Data> 
            <X> 
                <Values> 
                    <wijmo:ChartXData StringValue="데스크톱" /> 
                    <wijmo:ChartXData StringValue="노트북" /> 
                    <wijmo:ChartXData StringValue="일체형" />
                    <wijmo:ChartXData StringValue="태블릿PC" />
                    <wijmo:ChartXData StringValue="전화" />
                </Values>
            </X>
            <Y>
                <Values>
                    <wijmo:ChartYData DoubleValue="5" />
                    <wijmo:ChartYData DoubleValue="3" />
                    <wijmo:ChartYData DoubleValue="4" />
                    <wijmo:ChartYData DoubleValue="7" />
                    <wijmo:ChartYData DoubleValue="2" />
                </Values>
            </Y>
        </Data>
    </wijmo:BarChartSeries>
</SeriesList>
```

위의 과정을 통해, 다음의 그림과 같은 결과를 얻을 수 있습니다.

![](https://www.grapecity.co.kr/images/training/c1/tc4-2-1.png)

  

본문Demo의 소스 코드는 다음과 같습니다：

[C1 Bar Chart 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1BarChart-Overview.zip)



## C1Candlestickchart 컨트롤 입문

[Candle stick Chart 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/TestCandlestickChart.zip)

ComponentOne을 사용하는  C1Candlestickchart  컨트롤은 쉽게 주식차트를 작성할 수 있습니다! 아래는 주식차트 작성을 위한 구체적인 방법입니다.

  

**Step1**

먼저 ASP.Net Web 응용 프로그램을 만든 후 Web 폼을 추가합니다. 그리고 툴 바에서  C1CandlestickChart  컨트롤을 찾습니다. 툴 바에 C1CandlestickChart가 없는 경우 오른쪽을 클릭하고  “옵션”을 선택하여 C1CandlestickChart를 추가시킵니다.

  

**Step2**

도구상자에서  C1CandlestickChart  컨트롤을 Web 폼으로 드래그합니다. 컨트롤을 클릭하여 C1CandlestickChart 작업 메뉴를 열고  SreiesList를 선택합니다.

  

![](https://www.grapecity.co.kr/images/training/c1/tc4-3-1.png)

추가를 클릭하고 오른 쪽 바의 Date의 Close, High, Low, Open, X값을 수정합니다.

  

Low의 값을 각각 설정:

7.5,8.6,4.4,4.2,8,9,11,10,12.2,12,16,15.5,16,15,16,16.5,16,16,15,14.5,  
14,13.5,13,12,11,11,10,9,8,7.5,7.9,7.5,8.6,4.4,4.2,8,9,11,10,12.2,12,16,15.5,16

  

High의 값을 각각 설정:

10,12,11,14,16,20,18,17,17.5,20,22,21,22.5,20,21,20.8,20,19,18,  
17,16,15,15,14,13,12, 11.5,10.9,10,9,9.5,10,12,11,14,16,20,18,17,17.5,20,22,21,22.5

  

Open의 값을 각각 설정:

8,8.6,11,6.2,13.8,15,14,12,16,15,17,18,17.2,18.5,17.8,18.6,19.8,18,16.9,15.6,14.7,  
14.2, 13.9,13.2, 12.8,11.7,11.2,10.5,9.4,8.9,8.4,8,8.6,11,6.2,13.8,15,14,12,16,15,17,18,17.2

  

Close의 값을 각각 설정:

8.6,11,6.2,13.8,15,14,12,16,15,17,18,17.2,18.5,17.8,18.6,19.8,18,16.9,15.6,14.7,  
14.2,13.9,13.2, 12.8,11.7,11.2,10.5,9.4,8.9,8.4,8,8.6,11,6.2,13.8,15,14,12,16,15,17,18,17.2,18.5

  

X의 값은 2011-12-01부터2012-01-31까지입니다.

  

![](https://www.grapecity.co.kr/images/training/c1/tc4-3-2.png)

  

소스코드는 다음과 같습니다：

```csharp
<Data>
<Low DoubleValues="7.5,8.6,4.4,4.2,8,9,11,10,12.2,12,16,15.5,16,15,16,16.5,16,16,15,14.5,14,13.5,13,12,11,11,10,9,8,7.5,7.9,7.5,8.6,4.4,4.2,8,9,11,10,12.2,12,16,15.5,16" />
<High DoubleValues="10,12,11,14,16,20,18,17,17.5,20,22,21,22.5,20,21,20.8,20,19,18,17,16,15,15,14,13,12,11.5,10.9,10,9,9.5,10,12,11,14,16,20,18,17,17.5,20,22,21,22.5" />
<Open DoubleValues="8,8.6,11,6.2,13.8,15,14,12,16,15,17,18,17.2,18.5,17.8,18.6,19.8,18,16.9,15.6,14.7,14.2,13.9,13.2,12.8,11.7,11.2,10.5,9.4,8.9,8.4,8,8.6,11,6.2,13.8,15,14,12,16,15,17,18,17.2" />
<Close DoubleValues="8.6,11,6.2,13.8,15,14,12,16,15,17,18,17.2,18.5,17.8,18.6,19.8,18,16.9,15.6,14.7,14.2,13.9,13.2,12.8,11.7,11.2,10.5,9.4,8.9,8.4,8,8.6,11,6.2,13.8,15,14,12,16,15,17,18,17.2,18.5" />
</Data>

<X>
<Values>
<wijmo:ChartXData DateTimeValue="2011-12-01" />
<wijmo:ChartXData DateTimeValue="2011-12-02" />
<wijmo:ChartXData DateTimeValue="2011-12-05" />
<wijmo:ChartXData DateTimeValue="2011-12-06" />
<wijmo:ChartXData DateTimeValue="2011-12-07" />
<wijmo:ChartXData DateTimeValue="2011-12-08" />
<wijmo:ChartXData DateTimeValue="2011-12-09" />
<wijmo:ChartXData DateTimeValue="2011-12-12" />
<wijmo:ChartXData DateTimeValue="2011-12-13" />
<wijmo:ChartXData DateTimeValue="2011-12-14" />
<wijmo:ChartXData DateTimeValue="2011-12-15" />
<wijmo:ChartXData DateTimeValue="2011-12-16" />
<wijmo:ChartXData DateTimeValue="2011-12-19" />
<wijmo:ChartXData DateTimeValue="2011-12-20" />
<wijmo:ChartXData DateTimeValue="2011-12-21" />
<wijmo:ChartXData DateTimeValue="2011-12-22" />
<wijmo:ChartXData DateTimeValue="2011-12-23" />
<wijmo:ChartXData DateTimeValue="2011-12-26" />
<wijmo:ChartXData DateTimeValue="2011-12-27" />
<wijmo:ChartXData DateTimeValue="2011-12-28" />
<wijmo:ChartXData DateTimeValue="2011-12-29" />
<wijmo:ChartXData DateTimeValue="2011-12-30" />
<wijmo:ChartXData DateTimeValue="2012-01-02" />
<wijmo:ChartXData DateTimeValue="2012-01-03" />
<wijmo:ChartXData DateTimeValue="2012-01-04" />
<wijmo:ChartXData DateTimeValue="2012-01-05" />
<wijmo:ChartXData DateTimeValue="2012-01-06" />
<wijmo:ChartXData DateTimeValue="2012-01-09" />
<wijmo:ChartXData DateTimeValue="2012-01-10" />
<wijmo:ChartXData DateTimeValue="2012-01-11" />
<wijmo:ChartXData DateTimeValue="2012-01-12" />
<wijmo:ChartXData DateTimeValue="2012-01-13" />
<wijmo:ChartXData DateTimeValue="2012-01-16" />
<wijmo:ChartXData DateTimeValue="2012-01-17" />
<wijmo:ChartXData DateTimeValue="2012-01-18" />
<wijmo:ChartXData DateTimeValue="2012-01-19" />
<wijmo:ChartXData DateTimeValue="2012-01-20" />
<wijmo:ChartXData DateTimeValue="2012-01-23" />
<wijmo:ChartXData DateTimeValue="2012-01-24" />
<wijmo:ChartXData DateTimeValue="2012-01-25" />
<wijmo:ChartXData DateTimeValue="2012-01-26" />
<wijmo:ChartXData DateTimeValue="2012-01-27" />
<wijmo:ChartXData DateTimeValue="2012-01-30" />
<wijmo:ChartXData DateTimeValue="2012-01-31" />
</Values>
</X>
```

  

**Step3**

SreiesStyles을 선택하고 CandlestickCharts의 외관을 설정합니다. 이 예시에서  Close-Fill-Color설정을 Blue로 하고  Close-Width  설정을 5로 합니다. 순서대로  FallingClose, HighLow, Open, RisingClose, UnchangeClose를 설정합니다.

![](https://www.grapecity.co.kr/images/training/c1/tc4-3-3.png)

  

소스코드는 다음과 같습니다. ：

```csharp
<HighLow Width="2">
    <Fill Color="#8C8C8C"></Fill>
</HighLow>
<FallingClose Width="6">
    <Fill Color="#F07E6E"></Fill>
</FallingClose>
<RisingClose Width="6">
    <Fill Color="#90CD97"></Fill>
</RisingClose>
```

  

**Step4**

소스보기에서 차트 좌표축의 외관을 변경할 수 있습니다. 이 예시는 다음과 같이 코드를 변경한 것입니다：

```csharp
<Axis>
    <X>
        <GridMajor Visible="True"></GridMajor>
 
        <GridMinor Visible="True"></GridMinor>
        <TickMajor Position="Cross">
        </TickMajor>
    </X>
 
    <Y Visible="False" Compass="West">
        <Labels TextAlign="Center"></Labels>
 
        <GridMajor Visible="True"></GridMajor>
 
        <GridMinor Visible="False"></GridMinor>
    </Y>
</Axis>
```

이제 CandlestickChart의 작성이 완료되었습니다. 실행 결과는 다음과 같습니다. ：

  

![](https://www.grapecity.co.kr/images/training/c1/tc4-3-4.png)

본문Demo의 소스 코드는 다음과 같습니다：

[Candle stick Chart 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/TestCandlestickChart.zip)


## C1BubbleChart를 사용하여 쉽게 버블 차트를 만드는 방법

[C1 Bubble Chart 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1BubbleChart-overview.zip)

ASP.NET의 C1BubbleChart 컨트롤은 버블 차트를 쉽게 만들고 편리하게 3D데이터를 표시합니다. 본문에서는 어떻게 쉽게 버블차트를 만드는지를 소개합니다. 본문의 Demo에 구현을 위한 상세코드가 있습니다.

페이지에 C1BubbleChart컨트롤을 추가합니다.

C1BubbleChart 설정

  

C1BubbleChart.ChartLabel를 통해 폰트 크기, 문자형식, 위치 등 버블차트 레이블의 스타일을 설정합니다.  
C1BubbleChart.Aimation을 통해 애니메이션 및 애니메이션 딜레이 등의 표시방법을 설정합니다. 코드는 다음과 같습니다.

  

```csharp
<Animation Duration="500" Easing="EaseOutElastic"></Animation>
```

C1BubbleChart.Hint를 통해 툴팁 애니메이션 효과, 표시방법, 딜레이 등의 툴팁 및 툴팁 표시방법을 설정합니다.

C1BubbleChart 3D데이터 표시

C1BubbleChart에 시리즈를 추가하여 BubbleChartSeries를 만들고 C1BubbleChart.SeriesList를 통해 시리즈를 추가합니다. X, Y, Y1의 Values를 통해 3D데이터를 추가합니다. BubbleChartSeries.Label은 시리즈 레이블을 설정하는데 사용합니다.

```csharp
<serieslist>
    <wijmo:bubblechartseries label="서부">
        <data>
            <x>
	        <values>
		    <wijmo:chartxdata doublevalue="5" />
		    <wijmo:chartxdata doublevalue="14" />
		    <wijmo:chartxdata doublevalue="20" />
		    <wijmo:chartxdata doublevalue="18" />
		    <wijmo:chartxdata doublevalue="22" />
		</values>
	    </x>
            <y>
		<values>
		    <wijmo:chartydata doublevalue="5500" />
		    <wijmo:chartydata doublevalue="12200" />
		    <wijmo:chartydata doublevalue="60000" />
		    <wijmo:chartydata doublevalue="24400" />
		    <wijmo:chartydata doublevalue="32000" />
		    </values>
	    </y>
	    <y1 doublevalues="3,12,33,10,42">
		    <values>
		    <wijmo:charty1data doublevalue="3">/>
		    <wijmo:charty1data doublevalue="12">/>
		    <wijmo:charty1data doublevalue="33">/>
		    <wijmo:charty1data doublevalue="10">/>
		    <wijmo:charty1data doublevalue="42">/>
		    </values>
            </y1>
        </data>
    </wijmo:bubblechartseries>
</serieslist>
```

페이지 추가 로드 후 만든 버블차트의 실행 결과는 다음 그림과 같습니다. ：

![](https://www.grapecity.co.kr/images/training/c1/tc4-4-1.png)

  

본문Demo의 소스 코드는 다음과 같습니다：

[C1 Bubble Chart 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1BubbleChart-overview.zip)



## C1PieChart 파이 그래프 컨트롤의 도넛 그래프 작성\

[C1 Pie Chart - Donut 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1PieChart-donut.zip)

ASP.NET의 PieChart 컨트롤은 파이그래프를 작성할 수 있습니다. 파이그래프는 모든 시리즈마다 데이터 세그먼트를 만들고, 커스터마이즈 옵션과 애니메이션을 포함합니다.  
본문에서는 InnerRadius속성에 대한 설치를 통해 C1PieChart를 도넛 그래프로 전환하는 방법에 대해 소개합니다.

C1PieChart컨트롤을 페이지에 추가합니다.

C1PieChart 설정

C1PieChart.ShowChartLables를 통해 태그 표시여부를 설정합니다.

C1PieChart.Radius를 통해 파이 그래프의 반경을 설정합니다.

C1PieChart.InnerRadius 설정을 통해 법정 값으로 합니다. C1PieChart를 도넛 그래프로 전환시킵니다. 도넛 그래프 내 반경은 InnerRadius가 컨트롤합니다.

위의 내용을 설정할 수 있는 소스코드는 아래와 같습니다:

  

```csharp
<wijmo:C1PieChart runat = "server" ID="C1PieChart1" Radius="140" ShowChartLabels="false" 
Height="475" Width = "756" CssClass ="ui-widget ui-widget-content ui-corner-all" 
InnerRadius="40">
```

C1PieChart의 Hint를 통해 툴팁의 애니메이션 효과, 표시 방법, 딜레이 등 툴팁 및 어떻게 툴팁을 표시할지 여부를 설정합니다. 사이트에서 로드 후 마우스를 도넛 그래프의 데이터 세그먼트 위에 올리면 툴팁을 표시하게 됩니다.

```csharp
<Hint>
    <Content Function="hintContent" />
</Hint>
```

C1PieChart의 Legend를 통해 그래프의 예시를 설정합니다. 그 중 Legend.Text 설정 그래프의 예시 텍스트와 스타일을 포함합니다. 아래의 코드를 참고합니다. :

```csharp
<Legend Text="May 2009 - May 2010"></Legend>
```

  

### 데이터 세그먼트 작성

각기 다른 PieChartSeries 시리즈를 만들고 이 시리즈를 데이터 세그먼트로 작성하여 커스텀을 진행합니다.  
PieChartSeries의 Data를 사용하여 각 데이터 세그먼트의 데이터 값을 설정합니다.  
PieChartSeries의 HintContent를 사용하여 메시지 내용을 공지합니다.  
PieChartSeries의 Offset을 사용하여 데이터 세그먼트와 중심점의 오프셋 값을 설정합니다.  
마지막으로 모든 시리즈를 PieChart의 SeriesList에 추가시킵니다.

  

```csharp
<SeriesList>
    <wijmo:PieChartSeries Label="DX11GPU & WIN7" Data="5.6" Offset="30"></wijmo:PieChartSeries>
    <wijmo:PieChartSeries Label="iMac" Data="23.18"></wijmo:PieChartSeries>
    <wijmo:PieChartSeries Label="DX10GPU & WIN7" Data="56.36"></wijmo:PieChartSeries>
    <wijmo:PieChartSeries Label="DX10/11GPU & XP" Data="16.67"></wijmo:PieChartSeries>
    <wijmo:PieChartSeries Label="DX9 SM2b & 3.0" Data="11.77"></wijmo:PieChartSeries>
    <wijmo:PieChartSeries Label="DX9 SM 2 GPU" Data="4.34"></wijmo:PieChartSeries>
    <wijmo:PieChartSeries Label="DX8 GPU & BELOW" Data="5.13"></wijmo:PieChartSeries>
</SeriesList>
```

페이지를 로드하면 다음과 같은 도넛 그래프를 얻을 수 있습니다. 첨부파일의 Demo를 열면 상세한 정보를 얻을 수 있습니다.

  

![](https://www.grapecity.co.kr/images/training/c1/tc4-5-1.png)

  

본문Demo의 소스 코드는 다음과 같습니다：

[C1 Pie Chart - Donut 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/C1PieChart-donut.zip)


## C1BarChart 색 변경

[C1 Bar Chart 색 변경 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/BarChart_DifferentColors.zip)

C1BarChart 는 사용빈도가 가장 높은 컨트롤 중 하나입니다. 전형적인 활용법은 데이터 소스를 통해 그래프를 생성하고, X축과 Y축의 필드를 확정하는 것입니다. 최근 우리는 사용자의 요청을 받아 들여 데이터 설정을 하지 않은 그래프의 필드정보를 바탕으로 같은 시리즈의 데이터 바 색상을 설정하도록 했습니다.

  

아래 샘플의 데이터 소스는 모두 세 개의 필드가 있고 각각 Task와 Time 및 Status로 나눠집니다. Task 와 Time 각각은 X축과 Y축으로 설정되고, 막대그래프의 색상이 현재 Task의 완성상태를 나타냅니다. 최종적인 실행 결과는 다음의 그림과 같습니다.

  

![](https://www.grapecity.co.kr/images/training/c1/tc4-6-1.png)

C1BarChart가 status 필드를 바인딩하지 않으면 어떻게 현재 태스크의 이행 상태를 얻을 수 있을까요? 정답은 바로 C1GridView를 통하여 얻을 수 있다는 것입니다. 데이터를 C1GridView 컨트롤에 바인딩시켜, 포그라운드로부터 태스크 상태 정보를 얻을 수 있습니다. 그러므로 먼저 C1GridView의 데이터 소스를 설정해야 합니다.

  

```csharp
protected void Page_Load(object sender, EventArgs e)
{
   DataTable dt = new DataTable();
   dt.Columns.Add("Week", typeof(string));
   dt.Columns.Add("Time", typeof(double));
   dt.Columns.Add("Status", typeof(string));
  
   dt.Rows.Add("Wk1", 6, "Running");
   dt.Rows.Add("Wk1", 10, "Failed");
   dt.Rows.Add("Wk1", 19, "Failed");
   dt.Rows.Add("Wk1", 25, "Finished");
   dt.Rows.Add("Wk1", 7, "Running");
  
   C1BarChart1.DataSource = dt;
  
   C1ChartBinding cb = new C1ChartBinding();
   cb.XField = "Week";
   cb.XFieldType = ChartDataXFieldType.String;
   cb.YField = "Time";
   cb.YFieldType = ChartDataYFieldType.Number;
  
   C1BarChart1.DataBindings.Add(cb);
   C1BarChart1.DataBind();
  
   C1GridView1.DataSource = dt;
   C1GridView1.DataBind();
}
```

다음으로 C1GridView를 통해 포 그라운드에서 작업 상태를 가져와야합니다. 코드는 다음과 같습니다.

```csharp
var color = [];
$(document).ready(function () {
   var data = $("#C1GridView1").c1gridview("data");
   for (var i = 0; i < data.length; i++) {
      var status = data[i][2];
      if (status === "Running") {
         color.push("Yellow");
      }
      else if (status === "Finished") {
         color.push("Green");
      }
      else if (status === "Failed") {
         color.push("Red");
      }
   }
   $("#C1BarChart1").c1barchart({
      painted: function (args) {
         var count = $(this).data().fields.chartElements.bars.length;
         for (var i = 0; i < count; i++) {
            var bar = $(this).c1barchart("getBar", i);
            bar.attr({
               fill: color[i],
               stroke: "black"
            });
         }
         $(".wijmo-wijgrid").css("display", "none");
      },
      mouseOut: function (args) {
         var count = $(this).data().fields.chartElements.bars.length;
         for (var i = 0; i < count; i++) {
            var bar = $(this).c1barchart("getBar", i);
            bar.attr({
               fill: color[i],
               stroke: "black"
            });
         }
      }
   });
});
```

해당 기능의 모든 코드를 적용하면 위의 그림과 같이 실행됩니다. Demo를 통해 경험하실 수 있습니다. :

[C1 Bar Chart 색 변경 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/BarChart_DifferentColors.zip)


## C1LinearGauge와 C1RadialGauge 컨트롤 시작하기

C1LinearGauge컨트롤은 여러분이 원하는 정확한 그래픽 표현을 제공할 수 있습니다. 여러분은 수평, 수직 또는 경사 선형의 측량컨트롤을 선택할 수 있습니다.

C1RadialGauge컨트롤은 여러분이 원하는 정확한 그래픽 표현을 제공할 수 있습니다. 원형, 나선형, 호선형, 부채꼴이나 반원형의 대칭측량 컨트롤을 선택할 수 있습니다.

  

### C1LinearGauge 컨트롤의 사용

**Step1**

먼저,  ASP.Net Web응용프로그램을 만든 후  Web폼을 추가해야 합니다. 그리고 툴 바에서  C1LinearGauge컨트롤을 찾습니다. 툴 바에 C1LinearGauge가 없으면 오른쪽을 클릭하여 “옵션”에서 C1LinearGauge를 선택하여 추가합니다. 이 컨트롤을 더블 클릭하여 페이지에 추가합니다.

  

**Step2**

C1LinearGauge컨트롤의 속성 변경을 통해 원하는 효과를 적용할 수 있습니다.  
Behavior—value속성을 설정하여 미터기의 초기 값을 변경할 수 있습니다. Width와 Height속성을 통해 너비와 높이를 변경합니다. Face—FaceStyle—Fill—Color의 변경을 통해 색 채우기를 수정할 수 있습니다.  
이 속성들의 설정을 마친 후, 원하는 LinearGauge 타입을 선택하여 적용하면 완성됩니다. 실행하면 다음과 같이 표시됩니다. :

  

![](https://www.grapecity.co.kr/images/training/c1/tc4-7-1.png)

  

소스코드는 다음과 같습니다. ：

```csharp
<wijmo:C1LinearGauge ID="C1LinearGauge1" runat="server" Value="10" Width="500px">
    <TickMajor Factor="2" Visible="True" Offset="0" Interval="10"></TickMajor>
    <TickMinor Visible="False" Offset="0" Interval="5"></TickMinor>
    <Pointer Length="0.5" Width="4" Offset="0"></Pointer>
    <Animation Duration="2000" Easing="EaseOutBack"></Animation>
    <Face>
        <FaceStyle>
            <Fill Color="#CC66FF">
            </Fill>
        </FaceStyle>
    </Face>
</wijmo:C1LinearGauge>
```

  

### C1RadialGauge컨트롤의 사용

[C1 Gauge 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/TestGauge.zip)

**Step1**

항목 중에 새롭게 Web폼을 추가한 후, 툴 바에서 C1LinearGauge컨트롤을 찾습니다. 툴 바에 C1RadialGauge가 없으면 오른쪽을 클릭하여 “옵션”에서 C1RadialGauge를 선택하여 추가합니다. 이 컨트롤을 더블 클릭하여 페이지에 추가합니다.

  

실행하면 다음과 같이 표시됩니다. ：

![](https://www.grapecity.co.kr/images/training/c1/tc4-7-2.png)

  

**Step2**

앞에서는 기본 미터기를 추가했습니다. 이제 도형 미터기의 눈금 초기위치와 지침 초기위치를 설정합니다.

```csharp
<wijmo:C1RadialGauge ID="C1RadialGauge1" runat="server">
</wijmo:C1RadialGauge>
```

소스 코드를 변경합니다.：

```csharp
<wijmo:C1RadialGauge ID="C1RadialGauge1" runat="server" Value="50" Max="100" StartAngle="-45" SweepAngle="270">
</wijmo:C1RadialGauge>
```

실행하면 다음과 같이 표시됩니다. ：

![](https://www.grapecity.co.kr/images/training/c1/tc4-7-3.png)

  

**Step3**

미터기의 외관도 변경할 수 있습니다. `<wijmo:C1RadialGauge> </wijmo:C1RadialGauge>` 태그 사이에 아래의 코드를 추가하여 지침애니메이션 표시를 설정합니다. ：

```csharp
<Animation Duration="2000" Easing="EaseOutBack"></Animation>
```

아래의 코드를 추가하면 특별한 눈금을 정할 수 있습니다.

```csharp
<TickMajor Position="Inside" Factor="2" Visible="True" Offset="27" Interval="25"></TickMajor>
<TickMinor Position="Inside" Visible="True" Offset="30" Interval="5"></TickMinor>
```

실행 결과는 다음과 같습니다. ：

![](https://www.grapecity.co.kr/images/training/c1/tc4-7-4.png)

  

미터기 눈금반을 더 아름답게 만들 수 있습니다. 아래의 코드는 눈금반에 선을 그려 꾸민 것입니다. 실행 결과는 다음과 같습니다. ：

```csharp
<Ranges>
  <Wijmo:GaugelRange EndDistance="0.58" EndValue="10" EndWidth="5" StartDistance="0.6" StartValue="0" StartWidth="2">
  <RangeStyle Stroke="#7BA0CC" StrokeWidth="0">
  <Fill Color="#7BA0CC"></Fill>
  </RangeStyle>
  </Wijmo:GaugelRange>
  <Wijmo:GaugelRange EndDistance="0.54" EndValue="75" EndWidth="20" StartDistance="0.58" StartValue="10" StartWidth="5">
  <RangeStyle Stroke="White" StrokeWidth="0">
  <Fill ColorBegin="#B4D5F0" ColorEnd="#B4D5F0" Type="LinearGradient"></Fill>
  </RangeStyle>
  </Wijmo:GaugelRange>
  <Wijmo:GaugelRange EndDistance="0.5" EndValue="100" EndWidth="25" StartDistance="0.54" StartValue="175" StartWidth="20">
  <RangeStyle Stroke="#7BA0CC" StrokeWidth="0">
  <Fill Color="#7BA0CC"></Fill>
  </RangeStyle>
  </Wijmo:GaugelRange>
</Ranges>
```

![](https://www.grapecity.co.kr/images/training/c1/tc4-7-5.png)

  

원하는 대로 미터기가 완성되었습니다.

[C1 Gauge 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/TestGauge.zip)


## C1Sparkline컨트롤 시작하기

[C1 Sparkline 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/TestSparkline.zip)

C1Sparkline컨트롤은 한 줄로 정보의 주요 흐름을 나타냅니다. 미니 차트는 데이터를 볼 수 있게 해주는 작은 그래프로 구성되어 있으며 기존 차트처럼 공간을 차지하지 않습니다. 일반적으로 정보센터 게시판이나 테이블의 셀에 삽입됩니다.

  

**Step1**

먼저, ASP.Net Web응용프로그램을 만든 후 Web 폼을 추가해야 합니다. 그리고 툴 바에서 C1Sparkline컨트롤을 찾습니다. 툴 바에 C1Sparkline가 없으면 오른쪽을 클릭하여 “옵션”에서 C1Sparkline를 선택하여 추가합니다. 이 컨트롤을 더블 클릭하여 페이지에 추가합니다.

  

**Step2**

해당 컨트롤의 속성을 열어 Width속성 값은 200 px, Height속성 값은 50px으로 설정합니다. 또 기타 속성을 설정할 수 있고 컨트롤의 테마를 변경할 수도 있습니다. Theme 값을 Rocket으로 선택합니다, 설계도표에서 컨트롤의 태스크 메뉴를 열어 Edit Series를 선택하고 Sparkline Series 통합에디터를 엽니다. 오른 쪽 칸의 Type 값을 Area로 설정합니다. 자세한 것은 아래 그림을 참조합니다. ：

  

![](https://www.grapecity.co.kr/images/training/c1/tc4-8-1.png)

  

소스코드는 다음과 같습니다. ：

```csharp
<C1Sparkline:C1Sparkline ID="Sparkline1" runat="server">
      <Animation Duration="800" />
      <SeriesList>
          <C1Sparkline:SparklineSeries Bind="Score" Type="Area">
              <SeriesStyle Fill-Color="Orange" Stroke="Orange"></SeriesStyle>
          </C1Sparkline:SparklineSeries>
          <C1Sparkline:SparklineSeries Bind="Mood" Type="Line">
              <SeriesStyle StrokeWidth="2"></SeriesStyle>
          </C1Sparkline:SparklineSeries>
      </SeriesList>
</C1Sparkline:C1Sparkline>
```

  

**Step3**

계속해서 데이터를 설정해봅시다. 코드에 데이터를 직접 입력하면 됩니다.

```csharp
var data1 = new[]{
    new { Name="a",Score=73 ,Mood=66},
    new { Name="b",Score=95 ,Mood=50},
    new { Name="c",Score=89 ,Mood=65},
    new { Name="d",Score=66 ,Mood=70},
    new { Name="e",Score=50 ,Mood=43},
    new { Name="f",Score=65 ,Mood=65},
    new { Name="g",Score=70 ,Mood=27},
    new { Name="h",Score=43 ,Mood=77},
    new { Name="i",Score=65 ,Mood=58},
    new { Name="j",Score=27 ,Mood=73},
    new { Name="k",Score=77 ,Mood=95},
    new { Name="m",Score=45 ,Mood=89},
    new { Name="n",Score=84 ,Mood=19},
    new { Name="0",Score=48 ,Mood=89},
    new { Name="p",Score=58 ,Mood=69}
};

Sparkline1.Theme = "midnight";
Sparkline1.Height = 250;
Sparkline1.Width = 400;
Sparkline1.Animation.Easing = "bounce";
Sparkline1.DataSource = data1;
Sparkline1.DataBind();
```

이 예시는 아래의 코드를 실행한 것으로 다음 그림과 같이 나타납니다. ：

![](https://www.grapecity.co.kr/images/training/c1/tc4-8-2.png)

  

ValueAxis의 값도 설정할 수 있습니다. False로 설정 시 보이지 않게 되며 True로 설정하면 하나의 수치 축을 표시하여 플러스 마이너스 값을 구분하도록 합니다. 실행결과는 다음과 같습니다. ：

  

![](https://www.grapecity.co.kr/images/training/c1/tc4-8-3.png)

  

Type속성의 변경을 통해 기둥형 그래프와 선형 그래프를 표시할 수 있습니다.

  

![](https://www.grapecity.co.kr/images/training/c1/tc4-8-4.png)

  

<Animation Easing="bounce" />를 통해 애니메이션 효과를 추가할 수 있습니다. 이것은 탄성회복효과입니다.

  

완전한 소스코드는 다음과 같습니다. ：

[C1 Sparkline 샘플 다운로드](https://www.grapecity.co.kr/files/C1/Samples/C1ASP.NET/TestSparkline.zip)