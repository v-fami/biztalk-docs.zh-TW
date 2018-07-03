---
title: 指派權限 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b736fc7eb84964f9c0e74a3c319c9de1f3a3a44
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989671"
---
# <a name="assigning-rights"></a>指派權限
文件庫，針對上述主題中所建立的每個站台群組應該授與下列權限：  


|                                         文件庫                                         |                                   網站群組                                   | 要套用的自訂文件庫權限 |
|--------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------|----------------------------------------------|
|                                    範本文件庫                                    | Payments_Creators<br /><br /> Payments_Repairers<br /><br /> Payments_Approvers |                  檢視項目                  |
|                                     未剖析 （下面的詳細資料）                                     |                               Payments_Repairers                                |       檢視、 插入、 編輯、 刪除項目       |
|                              新的 SWIFT MT 訊息 （下面的詳細資料）                               |                                Payments_Creators                                |       檢視、 插入、 編輯、 刪除項目       |
|                              新的 SWIFT MX 訊息 （下面的詳細資料）                               |                                Payments_Creators                                |       檢視、 插入、 編輯、 刪除項目       |
|                                        Payments_Repairers                                        |                               Payments_Repairers                                |       檢視、 插入、 編輯、 刪除項目       |
|                                        Payments_Approvers                                        |                               Payments_Approvers                                |       檢視、 插入、 編輯、 刪除項目       |
| [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Outbox | Payments_Creators<br /><br /> Payments_Repairers<br /><br /> Payments_Approvers |       檢視、 插入、 編輯、 刪除項目       |

## <a name="unparsed-document-library"></a>未剖析的文件庫  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Message Repair 程序會處理無法以特殊方式剖析的訊息。 未剖析的訊息 （無法轉譯為 XML 的訊息） 會路由傳送至單一未剖析的訊息文件庫。 未剖析的文件庫應該限制為允許只有特定人員，而不是整個群組，來存取資料夾中。 這可確保未剖析的資料夾是盡可能安全。  

 若要修復未剖析的訊息的權限的使用者需要至少一個部門，定義在 MMC 的 [設定] 主控台，修復角色中的權限，也必須註冊在 NT 群組[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]Users 群組。  

## <a name="new-swift-mt-mx-messages-document-library"></a>新的 SWIFT MT / MX 訊息文件庫  
 新的 SWIFT MT 訊息及新的 SWIFT MX 訊息文件庫會在部署 MRSR 站台時建立。 新的 SWIFT MT 訊息及新的 SWIFT MX 訊息文件庫會儲存新的 SWIFT XML 範本或 「 重複使用 」 的訊息。 若要建立新的 SWIFT InfoPath XML 格式表示的訊息，您可以使用這些訊息。 這些訊息會上傳到新的 SWIFT MT 訊息及新的 SWIFT MX 訊息文件庫使用者按一下文件庫中的 [上傳] 按鈕。 您可以進一步將新的 SWIFT 訊息範本，來限制對指定的使用者存取。 若要這樣做您第一次建立新的文件庫，並複製所需的文件庫的 XML 範本。  

 如需有關 FormPublish 工具的詳細資訊，請參閱[FormPublish 工具](http://msdn.microsoft.com/09a6ed31-5917-4776-9a5e-955af440cdac)工具 區段中。