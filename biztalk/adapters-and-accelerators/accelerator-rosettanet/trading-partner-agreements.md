---
title: 交易夥伴協議 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- trading partners, agreements
- agreements, trading partners
ms.assetid: 846466d2-db39-42ba-8be1-ecca83a55a02
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26c8ac38e9b3dd0c32b496f3f7750fa0dcd982a1
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "22208678"
---
# <a name="trading-partner-agreements"></a>交易夥伴協議
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 交易夥伴協議 (TPA) 來處理與夥伴的訊息交換。 TPA 定義兩個交易夥伴之間訊息處理及驗證的規格。 它定義了這些交易夥伴實作相關交易夥伴介面程序 (PIP) 的方式，指定所有特定訊息類型實作的訊息內容。 TPA 也定義交易夥伴在網際網路上交換訊息的規格。  
  
## <a name="trading-partner-agreement-contents"></a>交易夥伴協議內容  
 每個交易夥伴協議包含下列資訊：  
  
-   交易夥伴的身份識別  
  
-   公開程序，由 RosettaNet 實作架構 (RNIF) 版本所定義，每個 TPA 會參考單一公開程序以啟動或回應 PIP 動作  
  
-   程序組態設定檔，此為 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 的 PIP 實作  
  
-   ASPX 設定，包括動作 URL、信號 URL 和同步 URL  
  
-   編碼和加密的通訊協定  
  
-   自訂屬性  
  
 若要建立交易夥伴協議，您必須使用 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台建立程序組態。 組態通常是以 RosettaNet PIP 為基礎，但是您也可以根據自訂的結構描述建立組態。 您也必須使用主控台來建立主要組織和夥伴。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 不支援未知合作對象之間交換訊息。 建立組態及組織之後，接著，您可以使用管理主控台建立交易夥伴協議。  
  
### <a name="process-configuration"></a>程序組態  
 這些設定決定 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 處理訊息內容的方式。 它們會指定 RosettaNet PIP，並指示 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 如何實作 PIP。 為了達成上述目的，這些設定為 PIP 指定的行為設定提供特定值，例如逾時值及重試值。 因此，兩個不同組的交易夥伴或同一組交易夥伴便能以兩種不同的方式實作相同的 PIP。  
  
 這些設定也會指定標準 (RosettaNet 或 CIDX)，以及主要組織和交易夥伴兩個角色的一般層面。 您也可以建立非 RosettaNet 內容的程序組態。 若要這樣做，必須建立該內容的結構描述，再根據結構描述建立組態。 對於非 RosettaNet 內容，您必須輸入訊息標準 」、 「 標準版本 」 和 「 承載繫結識別碼設定**一般**索引標籤中**程序組態設定** 對話方塊。 您只能使用 RNIF 2.0 傳輸非 RosettaNet 內容。  
  
 如需有關如何設定這些屬性的詳細資訊，請參閱[如何建立或編輯程序組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)。  
  
### <a name="home-organization"></a>主要組織  
 這些設定定義即將初始化訊息的主要組織。 這些設定包含「全球商務識別碼」(Global Business Identifier，GBI)，這是商業唯一識別碼的 DUNS 編號，另外還包含某些交易所需的連絡資訊。 如需有關如何設定這些屬性的詳細資訊，請參閱[建立或編輯主要組織](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md)。  
  
### <a name="partner-organization"></a>夥伴組織  
 這些設定會定義將會接收及回應訊息的夥伴。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 驗證每個內送 RNIF 訊息來自有效的合作對象有協議與主要組織。 如果不是，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 將無法進行驗證，並且也不會處理訊息。 如需有關如何設定這些屬性的詳細資訊，請參閱[建立或編輯夥伴](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md)。  
  
### <a name="agreements-trading-partner-agreement-variables"></a>協議 (交易夥伴協議變數)  
 協議指定交易夥伴關係的所有層面。 它指定程序組態設定的顯示代碼，如 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台所定義。 它也指定 RNIF 版本、連接埠 URL、通訊協定設定 (編碼和加密) 及其他變數。 如需有關如何設定這些屬性的詳細資訊，請參閱[建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)。  
  
 如需有關 [管理] 主控台的詳細資訊，請參閱[管理設定、 憑證、 資料庫和安全性](manage-configuration-certificates-databases-security.md)。 您也可以透過「開發人員參考」的 Microsoft.Solutions.BTARN.ConfigurationManager 命名空間中的類別及介面，以唯讀方式用程式存取這些設定。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Accelerator for RosettaNet 新增至 BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)   
 [RNIF 管線](../../adapters-and-accelerators/accelerator-rosettanet/rnif-pipelines.md)   
 [如何建立或編輯程序組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)   
 [建立或編輯主要組織](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md)   
 [建立或編輯夥伴](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md)   
 [建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)