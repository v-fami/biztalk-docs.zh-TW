---
title: "執行 SSO Projects1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO projects
- running SSO projects
- samples, SSO projects
ms.assetid: f8da1874-7495-47cd-a3a3-881f722c80a2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac9286dbaaced073dc7517bf5731fab3fa332d1c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-sso-projects"></a>執行 SSO 專案
您可以從 Internet Explorer 執行範例。  
  
## <a name="running-a-sample-from-internet-explorer"></a>從 Internet Explorer 執行範例  
  
#### <a name="to-run-the-sample-from-the-internet-explorer"></a>若要從 Internet Explorer 執行範例  
  
1.  開啟瀏覽器。  
  
2.  請使用下列語法：  
  
    ```  
    http://localhost/SSODemo/BTSHTTPReceive.dll?[Insert XML Instance body]   
    ```  
  
     例如：  
  
     http://localhost/SSODemo/BTSHTTPReceive.dll?\<ns0:method_list_method %20xmlns: ns0 ="http://microsoft.com/exposed/object/object1">\<ns0:method_list_method >\<ns1:method_list %20xmlns: ns1 ="http://microsoft.com/exposed/object">\<ns1:comp_code >\</ns1:comp_code >\<ns1:comp_name >\</ns1:comp_name >\< /ns1:object_1 >\</ns0:method_list >\</ns0:method_list_method >  
  
     在這種情況下，您不需要提供認證。  
  
## <a name="see-also"></a>另請參閱  
 [使用單一登入](../core/using-single-sign-on2.md)