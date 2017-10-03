---
title: "商務規則引擎安全性建議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, business rules
- Business Rules Framework, security
- business rules, security
ms.assetid: d5df1cd0-112a-4c72-b95d-cbcd1bc6a2c3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d7402a1cc36ef3d9473c3303da79b0c23f46bf8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="business-rule-engine-security-recommendations"></a>商務規則引擎安全性建議
商務規則引擎是商務規則架構的執行階段元件。 您可以使用商務規則架構，將易讀、宣告式且語意豐富的規則連接到任何商務物件 (.NET 元件)、XML文件或資料庫資料表。 如需商務規則架構的詳細資訊，請參閱[建立和使用商務規則](../core/creating-and-using-business-rules.md)。 如需 「 商務規則引擎的詳細資訊，請參閱[規則引擎](../core/rule-engine.md)。  
  
 商務規則引擎沒有 Windows 使用者群組，只有個別的帳戶。 BizTalk Server 使用兩個 SQL Sever 角色來限制對商務規則引擎資源的存取：  
  
 RE_Admin_Users SQL Server 角色適用於需要在商務規則引擎中執行系統管理工作 (例如部署規則) 的使用者。 RE_Admin_Users SQL Server  角色的成員包括 BizTalk 系統管理員。  
  
 RE_Host_Users 群組適用於不需要系統管理使用者權限，而只需執行讀取及執行規則等工作的其他所有商務規則引擎使用者。 RE_Host_Users 角色的成員包括 BizTalk_Host_Users 角色。 您可以使用 SQL Server 角色，實作商務規則引擎的權限，而不受 BizTalk Server 權限的影響。 如需有關使用 「 商務規則引擎所需的最低權限的詳細資訊，請參閱[最低安全性使用者權限](../core/minimum-security-user-rights.md)。 建議您依照下列指導方針來保護和部署您作業環境中的商務規則引擎執行階段。  
  
-   BizTalk Server 提供帳戶供您用來將更新服務登入安裝成服務權限，而且會將該帳戶新增到商務規則引擎資料庫上的 RE_Host_Users SQL Server 角色中。 如果您用來安裝的帳戶與要用來執行更新服務的帳戶不同，您必須從 RE_Host_Users SQL Server 角色中移除安裝帳戶。  
  
-   如果要使用更新服務元件，您必須將它安裝在所有 BizTalk 執行階段元件上。 為了從規則引擎資料庫擷取規則，更新服務會模擬服務的呼叫者。  
  
-   根據預設，所有的 BizTalk 主控件對規則引擎成品都擁有的相同的存取層次。 個別主控件並沒有獨立的安全性。 您可以使用規則引擎 API 設定個別原則的安全性。 如需如何設定個別原則安全性的詳細資訊，請參閱[商務規則架構安全性](../core/business-rules-framework-security.md)。  
  
## <a name="see-also"></a>另請參閱  
 [處理伺服器的連接埠](../core/ports-for-the-processing-servers.md)