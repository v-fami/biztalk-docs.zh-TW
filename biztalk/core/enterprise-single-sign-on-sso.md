---
title: "企業單一登入 (SSO) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, about SSO
- SSO
ms.assetid: beab96f7-f026-4ae1-8462-a165ad76bbec
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f6cbc5f514d13cd8457cd9417be5ea5b78408e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="enterprise-single-sign-on-sso"></a>企業單一登入 (SSO)
「企業單一登入」(SSO) 所提供的服務，可跨越本機與網路界限 (包含網域界限) 來儲存和傳輸加密的使用者認證。 SSO 將認證儲存在 SSO 資料庫中。 因為 SSO 提供的是一般的單一登入解決方案，所以中介軟體應用程式和自訂配接器都能利用 SSO 安全地在整個環境內儲存及傳輸使用者認證。 一般使用者不用再記住各個應用程式的不同認證了。  
  
 「單一登入」系統是由一個 SSO 資料庫、一個主要密碼伺服器，以及一或多個單一登入伺服器所組成。  
  
 SSO 系統包含*分支機構應用程式*系統管理員所定義。 *分支機構應用程式*是代表系統或子系統，例如主機、 後端系統或企業營運應用程式的邏輯實體您連接使用企業單一登入。 每個分支機構應用程式都有多個使用者對應；例如，它在 Active Directory 中使用者的認證與對應的 RACF 憑證之間具有對應。  
  
 SSO 資料庫是儲存分支機構應用程式相關資訊的 SQL Server 資料庫，另外也儲存了所有分支機構應用程式的所有已加密使用者認證。  
  
 *主要密碼伺服器*是儲存主要密碼的企業單一登入伺服器。 系統中所有其他「單一登入」伺服器會從主要密碼伺服器取得主要密碼。  
  
 SSO 系統也含有一或多個 SSO 伺服器。 這些伺服器會進行 Microsoft Windows 及後端憑證的對應，以及查詢 SSO 資料庫中的憑證。 系統管理員會使用它們來維護 SSO 系統。  
  
 更完整查詢在企業單一登入，請參閱[瞭解 SSO](../core/understanding-sso.md)。  
  
## <a name="see-also"></a>另請參閱  
 [執行階段架構](../core/runtime-architecture.md)