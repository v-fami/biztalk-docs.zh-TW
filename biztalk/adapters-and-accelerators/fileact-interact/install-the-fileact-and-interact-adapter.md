---
title: 安裝 FileAct 和 InterAct 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf387d59-373b-4151-9dfd-30c511978862
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5ee288b9772b7585fe972a4335e3cf8c5595024
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989383"
---
# <a name="install-the-fileact-and-interact-adapter"></a>安裝 FileAct 和 InterAct 配接器
本節提供安裝指示[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]– for SWIFT。 安裝配接器之前，您必須安裝先決條件軟體。  
  
## <a name="prerequisites"></a>必要條件  

* 使用屬於本機 administrators 群組的成員，以及 BizTalk Server 系統管理員群組的成員帳戶登入
  
## <a name="step-1-install-biztalk-server-and-configure-bam"></a>步驟 1： 安裝 BizTalk Server 和設定 BAM

1. 安裝[BizTalk Server 2016](../../install-and-config-guides/biztalk-server-2016-what-s-new-and-installation.md)，或[BizTalk Server 2013 R2 / 2013年](../../install-and-config-guides/biztalk-server-2013-and-2013-r2-what-s-new-install-and-upgrade.md)，並安裝商務活動監控 (BAM)。

2. 設定[BizTalk Server](../../install-and-config-guides/configure-biztalk-server.md)，並設定商務活動監控 (BAM)。
  
3. 請確定您有足夠的安全性權限可以存取[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 [最低安全性權限，以便讓 BizTalk Server](http://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)是絕佳的資源。
  
## <a name="step-2-install-biztalk-accelerator-for-swift-a4swift"></a>步驟 2： 安裝 BizTalk Accelerator for SWIFT (A4SWIFT)  

安裝和設定[BizTalk Accelerator for SWIFT](../../adapters-and-accelerators/accelerator-swift/install-configure-and-deploy-the-biztalk-accelerator-for-swift.md)。

  
## <a name="step-3-install-swiftalliance-gateway-sag"></a>步驟 3： 安裝 SWIFTAlliance 閘道 (SAG)  
 安裝 FileAct 和 InterAct 配接器之前，請建立 SAG 訊息合作夥伴、 端點和路由規則，並測試您在安裝 FileAct 和 InterAct 配接器的電腦上的 SAG 連線。

請參閱[ https://www.swift.com/our-solutions/interfaces-and-integration/alliance-gateway ](https://www.swift.com/our-solutions/interfaces-and-integration/alliance-gateway)的 SWIFTAlliance 閘道上的特定詳細資料。  

## <a name="step-4-install-the-biztalk-fileact-and-interact-adapters"></a>步驟 4： 安裝的 BizTalk FileAct 和 InterAct 配接器  
  
1. 執行**Setup.exe**以系統管理員身分來啟動安裝。  
  
2. 選取 [安裝]。  
  
3. 輸入您的使用者名稱和組織名稱，然後選取**下一步**。  
  
4. **接受**授權合約。
  
5. 在 **安裝選項**頁面上，執行下列其中之一：  
  
   - 選取 **完成**安裝所有元件的 FileAct 和 InterAct 配接器的選項。  
  
   - 選取 **自訂**選項來選擇要安裝哪些元件。  
  
     確認 安裝位置，或選取**瀏覽**以選取不同的安裝位置。 選取 **[下一步]**。  
  
6. 在 **摘要**頁面上，選取**安裝**安裝列出的元件。  
  
   > [!NOTE]
   >  當**執行組態精靈**是選取 （預設值）， **Microsoft BizTalk FileAct 和互動的配接器組態**精靈會自動執行您所選取**完成**.  
  
7. 安裝完成時，選取**完成**。 

## <a name="next-steps"></a>後續的步驟

[設定 FileAct 和 InterAct 配接器](../../adapters-and-accelerators/fileact-interact/configure-the-fileact-and-interact-adapter.md)  
[範例 InterAct 和 FileAct 訊息](../../adapters-and-accelerators/fileact-interact/sample-interact-and-fileact-messages.md)  
[解除安裝 FileAct 和 InterAct 配接器](../../adapters-and-accelerators/fileact-interact/uninstall-or-repair-the-fileact-and-interact-adapter.md)  
[閱讀安裝已知問題](../../adapters-and-accelerators/fileact-interact/read-the-installation-known-issues.md)
  
## <a name="see-also"></a>另請參閱  
[開始使用 FileAct 和 InterAct 配接器](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md)  
[了解 FileAct 和 InterAct 配接器架構](../../adapters-and-accelerators/fileact-interact/understanding-fileact-and-interact-adapter-architecture.md)