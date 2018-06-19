---
title: 如何判斷目前的單一登入存取 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cab68dfc-27cd-4f7c-a0df-20c670306358
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b16fc1d1677fa1a8859c75b43be36de9209dbac0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249254"
---
# <a name="how-to-determine-current-single-sign-on-access"></a>如何判斷目前的單一登入存取
您需要為使用者執行的其中一個首要工作，就是判斷已為目前的使用者設定哪些附屬應用程式。 您可以呼叫 ISSOMapper.GetApplications 以執行此查詢。  
  
### <a name="to-query-the-single-sign-on-database-for-the-applications-available-to-the-current-user"></a>若要查詢單一登入資料庫中目前使用者可用的應用程式  
  
1.  建立新的 `ISSOMapper` 執行個體。  
  
     一般而言，`ISSOMapper` 是設計用來擷取單一登入 (SSO) 資訊的介面。 您很可能會在許多類似的查詢中使用 `ISSOMapper`。  
  
2.  呼叫 GetApplications 以擷取所有與目前使用者有關的應用程式。  
  
     GetApplications 只會自動傳回目前使用者的附屬應用程式。  
  
 下列程式碼範例將示範如何查詢「單一登入」資料庫。  
  
```  
private static string[] Applications=null;  
. . .  
public static string[] GetCurrentUserApplications()  
{  
   if(Applications==null)  
   {  
      string[] descs;  
      string[] contacts;  
      ISSOMapper mapper=new ISSOMapper();  
      mapper.GetApplications(out Applications, out descs, out contacts);  
   }  
   return Applications;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用企業單一登入進行程式設計](../core/programming-with-enterprise-single-sign-on.md)