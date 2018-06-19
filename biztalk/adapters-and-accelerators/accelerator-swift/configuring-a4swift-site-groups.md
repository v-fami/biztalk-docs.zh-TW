---
title: 設定 A4SWIFT 網站群組 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- site groups, creating
- creating, site groups
- security, user accounts
- user accounts, site groups
- site groups, user accounts
ms.assetid: ec2f3efe-439a-4018-ad94-5ab0fb2808ee
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0070f10819ebbde18cdeab9c3bd534ca74bfbcd9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209006"
---
# <a name="configuring-a4swift-site-groups"></a>設定 A4SWIFT 網站群組
您需要建立對應的網站群組鎖定 Message Repair 和 New Submission 設定期間建立的文件庫上的權限。 若要執行此動作與上一節中的範例，會移至 MRSR 站台 A4SWIFT 系統管理員，並將其設定下列網站群組中：  
  
-   Payments_Creators  
  
-   Payments_Repairers  
  
-   Payments_Approvers  
  
 針對每個網站群組應該套用下列權限：  
  
-   **檢視項目。** 檢視項目在清單中，文件庫中的文件、 檢視網頁討論區註解，以及設定電子郵件警示的清單。  
  
-   **檢視頁面。** 在網站上檢視頁面。  
  
 每個使用者參與付款部門的角色，您需要建立新的站台使用者，並將該使用者指派給對應至網站群組[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]MMC 設定期間建立的角色。