---
title: 如何對應單一登入認證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e847bde9-7a4c-4b81-8ad6-6a7cf23d19a1
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5534eb63d7b9586017d77ffd84606a842f12a48d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002895"
---
# <a name="how-to-map-single-sign-on-credentials"></a>如何對應單一登入認證
當您知道您的企業單一登入資料庫中具有附屬應用程式後，即可將使用者的認證對應至該應用程式。 將目前使用者的認證對應至附屬應用程式時，您必須合併使用 `ISSOMapper` 和 `ISSOMapping` 介面。  
  
### <a name="to-map-between-an-affiliated-application-and-user-credentials"></a>在附屬應用程式和使用者認證之間進行對應  
  
1. 建立 `ISSOMapper` 和 `ISSOMapping` 的新執行個體。  
  
2. 將 `ISSOMapping` 屬性設定為相關的值。  
  
    `ISSOMapping` 的相關屬性就是使用者的 Microsoft® Windows® 網域名稱、Windows 使用者名稱、附屬應用程式的名稱，以及外部使用者名稱。  
  
3. 呼叫 ISSOMapping.Create 以建立對應。  
  
    呼叫 `ISSOMapping.Create` 會將對應的本機複本傳送至企業單一登入伺服器。  
  
4. 呼叫 `ISSOMapper.SetExternalCredentials` 以設定對應的認證。  
  
5. 呼叫 `ISSOMapping.Enable` 以啟用對應。  
  
   下列範例說明如何在指定的企業單一登入應用程式與使用者之間新增對應。  
  
```  
public static bool AddMapping(string application, string user, string XU, string XP)  
{  
   try  
   {  
      // Set mapping.  
      ISSOMapper mapper=new ISSOMapper();  
      ISSOMapping mapping=new ISSOMapping();  
     string username=user.Substring(user.IndexOf('\\')+1);  
      string userdomain=user.Substring(0, user.IndexOf('\\'));  
      mapping.WindowsDomainName=userdomain;  
      mapping.WindowsUserName=username;  
      mapping.ApplicationName=application;  
      mapping.ExternalUserName=XU;  
      mapping.Create(0);  
      // Set credentials.  
      string[] credentials=new string[]{XP};  
      mapper.SetExternalCredentials(application, XU, ref credentials);  
      mapping.Enable(0);  
   }  
   catch  
   {  
      return false;  
   }  
   return true;  
      }  
```  
  
## <a name="see-also"></a>另請參閱  
 [企業單一登入程式設計](../core/programming-with-enterprise-single-sign-on.md)