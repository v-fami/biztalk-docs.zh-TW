---
title: 建立新的訊息範本 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, templates
- templates, creating
- creating, templates
ms.assetid: 8c601d2b-b7a5-4ac4-9d98-fd9960038340
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e89c34b29818ab053217b823c6f8a787ce50a15d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999831"
---
# <a name="creating-a-new-message-template"></a>建立新的訊息範本
您可以從現有的範本來建立新的訊息範本。 這可讓自訂的表單，例如一份標準的 SWIFT 表單已輸入一些資料上建立新的訊息執行個體的建立者。 使用新的範本，建立者沒有輸入所有使用的空白表單時所需的資料。  
  
 您可以建立新的範本從您已使用對應的現有範本所產生的訊息執行個體。 您將資料的欄位加入[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單 （如同您所建立的新訊息執行個體），然後儲存為新範本的 表單。  
  
### <a name="to-save-a-modified-existing-template-as-a-new-template"></a>若要儲存修改過的現有範本作為新範本  
  
1. 在 Internet Explorer 中，開啟 MRSR 網站http://localhost/sites/bassite。  
  
2. 按一下 [文件]。  
  
3. 在文件 頁面上，按一下**新的 SWIFT MT 訊息**文件庫。  
  
4. 在新的 SWIFT MT 訊息 頁面上，按一下包含您想要根據您的新範本的範本類別。  
  
5. 指向您想要根據您的新範本，按一下向右箭號，然後按一下範本**在 Microsoft Office InfoPath 中編輯**。  
  
6. 在[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]2007年 視窗中，在 [郵件] 表單中，輸入您想要範本的一部分的訊息資料。  
  
7. 按一下 **檔案**，然後按一下**另存新檔**。  
  
8. 在快顯視窗指出此表單包含驗證錯誤，按一下**是**。  
  
9. 在 另存新檔 對話方塊中，選取 在範本的資料夾**將儲存在**文字，然後再輸入中的檔案名稱**檔案名稱**文字方塊。 按一下 **[儲存]**。  
  
10. 關閉[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]新範本的表單。  
  
    > [!NOTE]
    >  若要從新的範本中建立訊息執行個體，請參閱[建立和提交新訊息](../../adapters-and-accelerators/accelerator-swift/creating-and-submitting-a-new-message.md)。