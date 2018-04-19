---
title: 發行 （建立新的訊息） 的 MX 訊息執行個體檔案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7e6cdf4-b9db-42be-a92d-10a7471e2c2d
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4082174428f177905527d0c648b4d7ad000dde36
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="publishing-the-mx-message-instance-file-creating-new-messages"></a>發行 MX 訊息執行個體檔案 （建立新的訊息）
**若要發行的 MX 訊息執行個體檔案：**  
  
1.  移至輸出資料夾的 InfoPath 表單範本，在上一個步驟中產生**...\\< MessageType\>\TemplateDS\InfoPath 表單範本**。  
  
2.  在 Internet Explorer 中，開啟**http://localhost/sites/BASSite/New%20SWIFT%20MX%20Messages**。  
  
3.  在新的 Swift MX 訊息視窗中，按一下 **上傳**。  
  
4.  在上傳文件視窗中，按一下 **瀏覽**。  
  
5.  在 [選擇檔案] 對話方塊中，移至輸出資料夾的 InfoPath 表單上一個步驟中產生**...\\< MessageType\>\TemplateDS\InfoPath 表單範本**。 選取\<MessageType\>.xml 檔案 pacs.004.001.01.xml，例如，然後按一下**開啟**。  
  
6.  在上傳文件視窗中，按一下 **確定**。  
  
7.  新增 MX SWIFT 訊息中： \<MessageType\>視窗中的，於命名空間中，輸入 **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMX_ \<MessageType\>**，然後按一下 **確定**.