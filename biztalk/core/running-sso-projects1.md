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
# <a name="running-sso-projects"></a><span data-ttu-id="7d6d6-102">執行 SSO 專案</span><span class="sxs-lookup"><span data-stu-id="7d6d6-102">Running SSO Projects</span></span>
<span data-ttu-id="7d6d6-103">您可以從 Internet Explorer 執行範例。</span><span class="sxs-lookup"><span data-stu-id="7d6d6-103">You can run the sample  from Internet Explorer.</span></span>  
  
## <a name="running-a-sample-from-internet-explorer"></a><span data-ttu-id="7d6d6-104">從 Internet Explorer 執行範例</span><span class="sxs-lookup"><span data-stu-id="7d6d6-104">Running a Sample from Internet Explorer</span></span>  
  
#### <a name="to-run-the-sample-from-the-internet-explorer"></a><span data-ttu-id="7d6d6-105">若要從 Internet Explorer 執行範例</span><span class="sxs-lookup"><span data-stu-id="7d6d6-105">To run the sample from the Internet Explorer</span></span>  
  
1.  <span data-ttu-id="7d6d6-106">開啟瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="7d6d6-106">Open your browser.</span></span>  
  
2.  <span data-ttu-id="7d6d6-107">請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="7d6d6-107">Use the following syntax:</span></span>  
  
    ```  
    http://localhost/SSODemo/BTSHTTPReceive.dll?[Insert XML Instance body]   
    ```  
  
     <span data-ttu-id="7d6d6-108">例如：</span><span class="sxs-lookup"><span data-stu-id="7d6d6-108">For example:</span></span>  
  
     <span data-ttu-id="7d6d6-109">http://localhost/SSODemo/BTSHTTPReceive.dll?\<ns0:method_list_method %20xmlns: ns0 ="http://microsoft.com/exposed/object/object1">\<ns0:method_list_method >\<ns1:method_list %20xmlns: ns1 ="http://microsoft.com/exposed/object">\<ns1:comp_code >\</ns1:comp_code >\<ns1:comp_name >\</ns1:comp_name >\< /ns1:object_1 >\</ns0:method_list >\</ns0:method_list_method ></span><span class="sxs-lookup"><span data-stu-id="7d6d6-109">http://localhost/SSODemo/BTSHTTPReceive.dll?\<ns0:method_list_method%20xmlns:ns0="http://microsoft.com/exposed/object/object1">\<ns0:method_list_method>\<ns1:method_list%20xmlns:ns1="http://microsoft.com/exposed/object">\<ns1:comp_code>\</ns1:comp_code>\<ns1:comp_name>\</ns1:comp_name>\< /ns1:object_1>\</ns0:method_list>\</ns0:method_list_method></span></span>  
  
     <span data-ttu-id="7d6d6-110">在這種情況下，您不需要提供認證。</span><span class="sxs-lookup"><span data-stu-id="7d6d6-110">In this case you do not have to provide the credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d6d6-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d6d6-111">See Also</span></span>  
 [<span data-ttu-id="7d6d6-112">使用單一登入</span><span class="sxs-lookup"><span data-stu-id="7d6d6-112">Using Single Sign-On</span></span>](../core/using-single-sign-on2.md)