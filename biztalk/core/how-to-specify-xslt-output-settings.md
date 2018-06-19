---
title: 如何指定 XSLT 輸出設定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4c541432-fd4e-41cc-8bcc-f570ce5df439
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1aa3eea4c3f2f4696d3dc1fdf8109aeddec3ff8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255334"
---
# <a name="set-map-compilation-and-output-settings"></a>設定對應編譯和輸出設定
BizTalk 對應工具中設定對應屬性。 

使用這些對應屬性，您可以設定如何編譯對應、 包含或排除 XML 宣告，以及設定的編碼方式。 

本主題會示範如何在地圖上設定這些屬性。

## <a name="set-the-map-level-compilation"></a>設定地圖層級編譯

**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** ，您選擇`XslTransform`或`XslCompiledTransform`類別來編譯您的對應。 

1. 在方格檢視中開啟您的對應。
2. 在對應工具方格中，按一下滑鼠右鍵，然後選取**屬性**。  
3. 設定**使用 XSL 轉換**屬性： 

    | 選項 | Description |
    | --- | --- |
    | 未定義 | 會使用 XslTransform 設定的登錄旗標： <ul><li>64 位元主控件執行個體：`HKLM\SOFTWARE\Microsoft\BizTalk Server\3.0\Configuration`</li><li>32 位元主控件執行個體，以及 Visual Studio 的 [測試對應] 功能：`HKLM\SOFTWARE\Wow6432Node\Microsoft\BizTalk Server\3.0\Configuration`</li></ul> | 
    | True | 對應層級編譯屬性設定為`XslTransform`（舊版的行為） | 
    | False | 對應層級編譯屬性設定為`XslCompiledTransform` | 

> [!NOTE] 
> 從 BizTalk Server 2013 開始，對應工具編譯行為已變更從`XslTransform`至`XslCompiledTransform`。 [對應工具更新意義您](http://www.quicklearn.com/blog/2013/05/24/what-the-biztalk-server-2013-mapper-updates-mean-for-you/)部落格文章提供絕佳說明的行為和其潛在的影響。 
> 
> 從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]，您可以選擇哪一個類別來編譯您的對應。 
  
## <a name="include-or-exclude-an-xml-declaration"></a>包含或排除 XML 宣告  
您可以選擇不論 XML 宣告是否為輸出。 

1. 在方格檢視中開啟您的對應。
2. 在對應工具方格中，按一下滑鼠右鍵，然後選取**屬性**。  
3. 在下拉式清單中**省略 XML 宣告**屬性選取**是**省略 XML 宣告。 選取**否**不以省略 XML 宣告。  

XML 宣告會出現 (如果您選取**否**) 與下列類似。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
```  
  
## <a name="set-encoding-for-output-instance-data"></a>設定編碼輸出執行個體資料  
編碼提供執行階段引擎所需的資訊，用以決定在建立對應的輸出結果時要使用哪個字元集。  
   
1. 在方格檢視中開啟您的對應。
2. 在對應工具方格中，按一下滑鼠右鍵，然後選取**屬性**。    
3.  在下拉式清單中**XSLT 編碼**屬性中，選取您要字元集用於輸出執行個體資料。  
  
## <a name="see-also"></a>另請參閱  
 [編譯和測試對應](../core/compiling-and-testing-maps.md)   
 [使用 BizTalk 對應工具](../core/using-biztalk-mapper.md)   
 [有效的 BizTalk 對應工具 XSLT 編碼類型](../core/valid-biztalk-mapper-xslt-encoding-types.md)