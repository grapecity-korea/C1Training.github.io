---
title: C1 배포 | Deploy
keywords: c1 배포, c1 deploy, c1 distribution
last_updated: Aug 08, 2019
summary: "컴포넌트원(ComponentOne)를 배포하는 방법에 대한 설명입니다."
sidebar: mydoc_sidebar
permalink: c1_deploy.html
folder: mydoc
---

배포가 될 때 사용중인 아래의 DLL이 같이 배포된 프로그램의 같은 경로에 포함되어야 합니다.

> - C1.Win.2.dll
> - C1.Win.컨트롤 이름.2.dll/C1.C1 컨트롤 이름.2.dll
> - C1.Win.4.dll
> - C1.Win. 컨트롤 이름.4.dll/C1.C1 컨트롤 이름.4.dll
> - C1.Win. 컨트롤 이름.4.Design.dll/C1.C1 컨트롤 이름.4.Design.dll

DLL에 붙어 있는 숫자 2와 4는 기본적으로 .NET 프레임 워크와 호환성을 나타내며 해당 DLL이 다양한 타입의 호환성을 가지기 때문에 현재는 문제가 되지 않더라도 장래적인 호환성을 위하여 배포하실 때는 2가지 버전의 DLL을 모두 배포하여야 합니다.

> 예를 들어 C1.Win.FlexGrid.2.dll와 C1.Win.FlexGrid.4.dll을 모두 배포하여야 합니다.

아래 링크를 통해 좀 더 자세한 사항을 확인해보실 수 있습니다.  
[https://help.grapecity.com/componentone/NetHelp/c1studiowinforms/webframe.html#Redistributable_Files.html](https://help.grapecity.com/componentone/NetHelp/c1studiowinforms/webframe.html#Redistributable_Files.html)
