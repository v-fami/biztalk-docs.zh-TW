---
title: 如何指定 XSLT 輸出設定 |Microsoft Docs
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
ms.openlocfilehash: 1d55a8ddccb996f11315c8856797147083da9123
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998031"
---
# <a name="set-map-compilation-and-output-settings"></a>設定對應編譯和輸出設定
設定 BizTalk 對應工具中的對應屬性。 

使用這些屬性對應，您可以設定如何編譯對應、 包含或排除 XML 宣告，以及設定的編碼方式。 

本主題說明如何設定這些屬性在地圖上。

## <a name="set-the-map-level-compilation"></a>設定對應層級的編譯

**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** ，您選擇`XslTransform`或`XslCompiledTransform`類別來編譯您的對應。 

1. 方格檢視中開啟您的對應。
2. 以滑鼠右鍵按一下對應工具方格中的任何位置，然後選取**屬性**。  
3. 設定**使用 XSL 轉換**屬性： 

    | 選項 | 描述 |
    | --- | --- |
    | 未定義 | 使用 XslTransform 設定的登錄旗標： <ul><li>64 位元主控件執行個體： `HKLM\SOFTWARE\Microsoft\BizTalk Server\3.0\Configuration`</li><li>32 位元主控件執行個體，以及 Visual Studio 的 [測試對應] 功能： `HKLM\SOFTWARE\Wow6432Node\Microsoft\BizTalk Server\3.0\Configuration`</li></ul> | 
    | True | 對應層級的編譯屬性設定為`XslTransform`（舊版行為） | 
    | False | 對應層級的編譯屬性設定為 `XslCompiledTransform` | 

> [!NOTE]
> 從 BizTalk Server 2013，對應工具編譯行為已變更從`XslTransform`至`XslCompiledTransform`。 [什麼 Mapper Updates Mean for You](http://www.quicklearn.com/blog/2013/05/24/what-the-biztalk-server-2013-mapper-updates-mean-for-you/)部落格文章提供詳細說明了行為，以及其潛在的影響。 
> 
> 從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]，您可以選擇哪一個類別來編譯您的對應。 
  
## <a name="include-or-exclude-an-xml-declaration"></a>包含或排除 XML 宣告  
您可以選擇是否 XML 宣告是否為輸出。 

1. 方格檢視中開啟您的對應。
2. 以滑鼠右鍵按一下對應工具方格中的任何位置，然後選取**屬性**。  
3. 中的下拉式清單**省略 XML 宣告**屬性中，選取**是**省略 XML 宣告。 選取  **No**不表示省略 XML 宣告。  

XML 宣告會出現 (如果您選取**No**) 如下所示。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
```  
  
## <a name="set-encoding-for-output-instance-data"></a>設定編碼方式輸出執行個體資料  
編碼提供執行階段引擎所需的資訊，用以決定在建立對應的輸出結果時要使用哪個字元集。  
   
1. 方格檢視中開啟您的對應。
2. 以滑鼠右鍵按一下對應工具方格中的任何位置，然後選取**屬性**。    
3.  中的下拉式清單**XSLT 編碼**屬性中，選取您要字元集用於輸出執行個體資料。  
  
## <a name="see-also"></a>另請參閱  
 [編譯和測試對應](../core/compiling-and-testing-maps.md)   
 [使用 BizTalk 對應工具](../core/using-biztalk-mapper.md)   
 [有效的 BizTalk 對應工具 XSLT 編碼類型](../core/valid-biztalk-mapper-xslt-encoding-types.md)