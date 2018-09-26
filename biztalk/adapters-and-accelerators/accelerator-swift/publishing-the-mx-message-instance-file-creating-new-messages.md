---
title: 發佈 MX 訊息執行個體檔案 （建立新的訊息） |Microsoft Docs
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
ms.openlocfilehash: 21c7894158bb245b746b9a53dcfc93d40b9f9e1d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970674"
---
# <a name="publishing-the-mx-message-instance-file-creating-new-messages"></a>發佈 MX 訊息執行個體檔案 （建立新的訊息）
**若要發佈 MX 訊息執行個體檔案：**  

1. 移至前一個步驟中產生的 InfoPath 表單範本的輸出資料夾 **...\\< MessageType\>\TemplateDS\InfoPath 表單範本**。  

2. 在 Internet Explorer 中，開啟**http://localhost/sites/BASSite/New%20SWIFT%20MX%20Messages**。  

3. 在新的 Swift MX 訊息視窗中，按一下**上傳**。  

4. 在上傳文件視窗中，按一下**瀏覽**。  

5. 在 [選擇檔案] 對話方塊中，移至前一個步驟中產生的 InfoPath 表單的輸出資料夾 **...\\< MessageType\>\TemplateDS\InfoPath 表單範本**。 選取  \<MessageType\>.xml 檔案等 pacs.004.001.01.xml，，，然後按一下**開啟**。  

6. 在上傳文件視窗中，按一下**確定**。  

7. 新增 SWIFT MX 訊息中： \<MessageType\>視窗中的，命名空間 方塊中，輸入<strong>http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMX_\<MessageType\></strong>，然後按一下**確定**。
