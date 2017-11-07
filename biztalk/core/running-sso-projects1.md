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
ms.openlocfilehash: ea316e8f2c78ff718d6821b3f5d063bd86621dd1
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
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
 [保護配接器](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)