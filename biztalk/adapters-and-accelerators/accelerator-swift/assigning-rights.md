---
title: "指派權限 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user accounts, assigning permissions
- security, user accounts
- document library, new messages
- document library, unparsed
- messages, document library
- privileges
- permissions
- unparsed document library
- security, permissions
ms.assetid: cee44240-aa00-4080-9e7f-728b2421102b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a980fde1a4aea5d2e741fa576e55e659c0835f9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="assigning-rights"></a>指派權限
文件庫，針對上述主題中建立每個網站群組上，應該被授與下列權限：  
  
|文件庫|網站群組|要套用的自訂文件庫權限|  
|----------------------|-----------------|--------------------------------------------------|  
|範本文件庫|Payments_Creators<br /><br /> Payments_Repairers<br /><br /> Payments_Approvers|檢視項目|  
|未剖析 （下列詳細資料）|Payments_Repairers|檢視、 插入、 編輯、 刪除項目|  
|新的 SWIFT MT 訊息 （下面的詳細資料）|Payments_Creators|檢視、 插入、 編輯、 刪除項目|  
|新的 SWIFT MX 訊息 （下面的詳細資料）|Payments_Creators|檢視、 插入、 編輯、 刪除項目|  
|Payments_Repairers|Payments_Repairers|檢視、 插入、 編輯、 刪除項目|  
|Payments_Approvers|Payments_Approvers|檢視、 插入、 編輯、 刪除項目|  
|[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Outbox|Payments_Creators<br /><br /> Payments_Repairers<br /><br /> Payments_Approvers|檢視、 插入、 編輯、 刪除項目|  
  
## <a name="unparsed-document-library"></a>未剖析的文件庫  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]訊息修復程序會處理無法以特殊方式剖析的訊息。 未剖析的訊息 （無法轉譯成 XML 的訊息） 會路由傳送至單一未剖析的訊息文件庫。 未剖析的文件庫應該限制為允許只有特定人員，而不是整個群組，來存取資料夾。 這可確保未剖析的資料夾是儘可能安全。  
  
 使用者擁有修復未剖析的訊息的權限定義在 MMC 的 [設定] 主控台，至少一個部門需要修復角色中的權限，也需要註冊在 NT 群組[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]Users 群組。  
  
## <a name="new-swift-mt-mx-messages-document-library"></a>新的 SWIFT MT / MX 訊息文件庫  
 MRSR 網站部署時，會建立新 SWIFT MT 訊息和新 SWIFT MX 訊息文件庫。 新的 SWIFT MT 訊息及新 SWIFT MX 郵件的文件庫儲存新的 SWIFT XML 範本或 「 重複使用 」 訊息。 若要建立新的 SWIFT InfoPath XML 格式表示的訊息，您可以使用這些訊息。 這些訊息上傳到新的 SWIFT MT 訊息及新 SWIFT MX 郵件的文件庫使用者按一下文件庫中的 [上載] 按鈕。 您可以進一步散發新 SWIFT 訊息範本來限制對指定的使用者存取。 若要這樣做您會先建立新的文件庫，然後再複製所需的文件庫中的 XML 範本。  
  
 如需 FormPublish 工具的詳細資訊，請參閱[FormPublish 工具](http://msdn.microsoft.com/en-us/09a6ed31-5917-4776-9a5e-955af440cdac)工具 > 一節中。