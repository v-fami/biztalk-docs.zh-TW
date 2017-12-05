---
title: "使用 BizTalk ESB Toolkit 公用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2dc05ac-831a-44e1-bd44-e41398552ab1
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db4a8ef2def05e0b77d272463d7a79f937623b1a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="using-the-biztalk-esb-toolkit-utilities"></a>使用 BizTalk ESB Toolkit 公用程式
本章節描述各種公用程式的一部分加入[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。  
  
 **ESB 路線匯入公用程式**  
  
 此公用程式位於 \bin 目錄之[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]稱為 EsbImportUtil.exe。 此公用程式可用來發行或部署到 ESBItineraryDB 資料庫 XML 路線。  
  
 此公用程式的語法如下所示：  
  
```  
>EsbImportUtil <Parameter1> <Value> <parameter2> <Value>...  
```  
  
 它可以接受各種參數如下所示：  
  
 /？:\<顯示說明的參數\>  
  
 /f:\<路線 xml 檔案路徑\>  
  
 包裝\<發行 &#124; 部署\>  
  
 /n:\<預設行程名稱\>  
  
 /v\<預設路線版本 （格式為 'major.minor'）\>  
  
 /o\<無訊息的覆寫\>  
  
 以下是如何使用此公用程式的範例。  
  
 若要發行到路線資料庫：  
  
```  
>EsbImportUtil /f:myitinerary.xml /c:published  
```  
  
 將部署至路線資料庫：  
  
```  
>EsbImportUtil  /f:myitinerary.xml /c:deployed  
```  
  
 **SSO 組態保存公用程式**  
  
 此公用程式位於 \bin 目錄之[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]稱為 Microsoft.Practices.ESB.PersistConfigurationTool.exe。 此公用程式可以用來保存到 BizTalk SSO 資料庫的 ESB 組態資訊。 這也可用來檢視組態資訊，以及從 SSO 資料庫中移除組態資訊。  
  
 此公用程式的語法如下所示：  
  
 **若要新增的組態區段：**  
  
```  
>Microsoft.Practices.ESB.PersistConfigurationTool  /P /F:app.config /S:SectionName /A:ApplicationName  
```  
  
> [!NOTE]
>  如果未提供 /S，就會加入下列各節： connectionStrings esb、 esb.resolver 和 cachingConfiguration。  
  
 **若要移除的區段：**  
  
```  
>Microsoft.Practices.ESB.PersistConfigurationTool  /R /S:SectionName  
```  
  
 若要檢視現有的區段，請與 /V 交換器搭配的應用程式和區段的參數。  
  
 若要設定系統管理員群組名稱，請使用 AG:AdminGroupName 交換器。  
  
 若要設定使用者群組名稱，請使用 UG:UserGroupName 交換器。