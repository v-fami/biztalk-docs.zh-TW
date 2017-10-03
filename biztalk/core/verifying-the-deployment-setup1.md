---
title: "驗證部署 Setup1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CLASSPATH, verifying
- deployment, verifying setup
ms.assetid: 6c719e4c-9a61-480f-a4e4-0a1c518d1364
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5799d164dc2470236c3ab0286e38d19986a4d5a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="verifying-the-deployment-setup"></a>驗證部署設定
使用 BizTalk Server 匯入繫結檔案之前，必須確認下列項目：  
  
-   CLASSPATH 指向 JD Edwards EnterpriseOne 專屬檔案的特定位置。 確認這些檔案的位置在新電腦上是相同的，否則請編輯繫結檔案。  
  
-   在新電腦上用於存放回應的資料夾存在且相同，否則請編輯繫結檔案。  
  
-   JD Edwards EnterpriseOne 系統密碼 (如果出現在組態中) 以 ***** 格式儲存在繫結檔案中。 如需詳細資訊，請參閱[部署限制](../core/deployment-limitations4.md)。  
  
## <a name="see-also"></a>另請參閱  
 [部署連接埠和組件](../core/deploying-ports-and-assemblies3.md)