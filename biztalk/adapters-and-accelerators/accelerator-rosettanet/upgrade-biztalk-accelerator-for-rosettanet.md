---
title: "升級 BizTalk Server 中的 RosettaNet 加速器 (BTARN) |Microsoft 文件 」"
description: "請依照下列升級步驟來更新到 BizTalk Server 中的目前版本的 BTARN"
author: MandiOhlinger
manager: anneta
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
ms.author: mandia
ms.openlocfilehash: 16e6083f3e5fb1778d77536cd602ee2208c0005f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="upgrade-the-rosettanet-accelerator"></a>升級 RosettaNet 加速器

## <a name="upgrade-overview"></a>升級概觀
您可以升級舊版安裝 BizTalk Accelerator for RosettaNet (BTARN) 的目前版本。 升級程序包括升級 BizTalk Server，然後升級 BTARN。  
  
 您可以從舊版的 BTARN 以升級執行 BTARN 安裝程式。 安裝程式會將 BTRAN 組態資訊移轉到最新版本。  
  
 在多伺服器 BTARN 環境中，您應升級所有 BizTalk 伺服器，然後再到 BTARN。 請依下列順序移轉您的伺服器：  
  
-   裝載 BizTalk 群組的伺服器  
  
-   每個處理節點  
  
-   BAM 入口網站伺服器  
  
 BTARN 中升級程序，請確定您執行下列作業：  
  
-   檢查 SQL Server (MSSQLSERVER) 服務是否正在執行。  
  
-   請勿執行無訊息安裝。  
  
## <a name="upgrade-steps"></a>升級步驟  
  
1.  升級 BizTalk Server。 請參閱[BizTalk Server 新安裝、 設定及升級](../../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md)。
  
2.  備份 BTARN 資料庫和 BTARN 訊息結構描述。  
  
    > [!NOTE]
    >  您應該備份基於安全理由 BTARN 資料庫。 安裝程式會將 BTRAN 資料庫移轉到較新版本。  
  
3.  備份之下任何檔案*< 磁碟機\>*: \Program Files\\Microsoft BizTalk Accelerator for RosettaNet 資料夾，您所做的變更，例如 SDK 中的檔案。  
  
4.  解除部署會參考所列之一或多個舊版 BTARN 組件的任何專案或組件。  
  
5.  在 Visual Studio 中，您必須手動解除部署所有的 BTARN 組件，以下列順序：  
  
    -   Microsoft.Solutions.BTARN.CommonTypes  
  
    -   Microsoft.Solutions.BTARN.GlobalSchemas  
  
    -   Microsoft.Solutions.BTARN.PipelineReceive  
  
    -   Microsoft.Solutions.BTARN.PipelineSend  
  
    -   Microsoft.Solutions.BTARN.PrivateInitiator  
  
    -   Microsoft.Solutions.BTARN.PrivateResponder  
  
    -   Microsoft.Solutions.BTARN.PublicInitiator  
  
    -   Microsoft.Solutions.BTARN.PublicResponder  
  
    -   Microsoft.Solutions.BTARN.Schemas.RNIFv11  
  
    -   Microsoft.Solutions.BTARN.Schemas.RNIFv20  
  
    -   Microsoft.Solutions.BTARN.Schemas.RNPIPs  
  
6.  執行 BTARN 安裝程式。 請參閱[安裝及設定 RosettaNet 加速器](install-configure-biztalk-accelerator-for-rosettanet.md)。
  
7.  使用**BTSTask.exe**手動重新部署 BTARN 組件，以下列順序的 (\Program Files\Microsoft BizTalk Server):  
  
    -   Microsoft.Solutions.BTARN.CommonTypes  
  
    -   Microsoft.Solutions.BTARN.GlobalSchemas  
  
    -   Microsoft.Solutions.BTARN.PipelineReceive  
  
    -   Microsoft.Solutions.BTARN.PipelineSend  
  
    -   Microsoft.Solutions.BTARN.PrivateInitiator  
  
    -   Microsoft.Solutions.BTARN.PrivateResponder  
  
    -   Microsoft.Solutions.BTARN.PublicInitiator  
  
    -   Microsoft.Solutions.BTARN.PublicResponder  
  
    -   Microsoft.Solutions.BTARN.Schemas.RNIFv11  
  
    -   Microsoft.Solutions.BTARN.Schemas.RNIFv20  
  
    -   Microsoft.Solutions.BTARN.Schemas.RNPIPs  
  
    > [!NOTE]
    >  如需有關**BTSTask.exe**，請參閱 BizTalk Server 說明中的 < BTSTask 命令列參考 > 主題。  
  
8.  重建任何專案或組件的參考一或多個 [BTARN 組件。 使用**BTSTask.exe**手動重新部署這些專案。  
  
9. 請將下列項目之 IIS 中的虛擬資料夾從 ASP.NET 2.0 升級到 ASP.NET 4.0：  
  
    -   BTARNApp  
  
    -   BTARNHttpReceive  
  
10. 重新啟動電腦，以套用所有修改。  
  
