---
title: "解除安裝 BizTalk Server 上的 BizTalk RosettaNet 加速器 (BTARN) |Microsoft 文件 」"
description: "解除部署成品，並取消設定 BTARN 以移除 BizTalk Server 加速器"
author: MandiOhlinger
manager: anneta
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
ms.author: mandia
ms.openlocfilehash: 8d289a3705eb0c127dc4d2637c2d6ffd3c122b36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="uninstall-the-rosettanet-accelerator"></a>解除安裝 RosettaNet 加速器

## <a name="before-you-begin"></a>開始之前
  
* 如果您只執行**Setup.exe**，解除安裝程序不會移除商務活動監控 (BAM) 成品、 BizTalk 成品、 網際網路資訊服務 (IIS) 虛擬目錄和應用程式集區。  
  
* 如果您使用**回送**公用程式來建立鏡像協議，針對單一電腦部署，然後執行該工具搭配**/停用 <** **home 組織** **>** 選項後再中刪除夥伴**BTARN 管理主控台**。  
  
* 如果此伺服器是多電腦部署的一部分，不會執行**BtarnClean**公用程式或手動解除部署 BTARN 組件。 一部電腦上移除成品會中斷其他電腦的功能。  如果您想要從所有伺服器解除安裝 BTARN，然後執行**BtarnClean**公用程式。 

  
## <a name="undeploy-the-artifacts"></a>解除部署成品  

我們建議您備份之前解除部署 BAM 成品。 

1. 解除部署您部署的所有 BAM 成品：  
  
    1.  在命令提示字元執行下列命令：  
  
         ```cd %ProgramFiles%\\<BizTalk Server installation directory\>\Tracking```
  
    2.  在已安裝追蹤 UI 的命令提示字元下，執行下列命令：  
  
         ```bm remove-all DefinitionFile:"%ProgramFiles%\\<installation directory\>\BAMTracking\tracking.xml"```
  
        > [!NOTE]
        >  如需有關 BAM 的詳細資訊，請參閱[管理商務活動監控](../../core/managing-bam.md) 
  
2.  備份並刪除在 BTARN 管理主控台中的所有合約、 合作夥伴和主要組織。 請參閱使用的相關資訊 （在 「 BTARN 說明 」 的 [作業] 節點中） 的 < 管理 BTARN 組態 > 主題**BtarnConfig**公用程式備份協議和夥伴。  
  
    > [!NOTE]
    >  * 停止和解除部署 BTARN 使用所建立的 BizTalk 成品[BtarnClean](btarnclean.md)公用程式。
    >  * 移除您部署的任何其他成品。 請參閱[解除部署 BizTalk 應用程式](../../core/undeploying-biztalk-applications.md)。
  
3.  從 BTARN 安裝程式中，尋找 MSI\Program Files\Microsoft BizTalk Accelerator for RosettaNet\SDK 資料夾。 在 SDK 資料夾中，按兩下**BTARNClean.exe**，然後選取**Y**若要繼續，或**N**取消執行公用程式。  
  
    > [!NOTE]
    >  如果您的伺服器是多電腦部署實例的一部分，可以略過步驟 3。 解除部署任何共用的資源將會中斷部署中其他伺服器的功能。  
  
4.  解除部署您所建立和部署的任何自訂組件。  
  
5.  在命令提示字元中，移至 files\microsoft BizTalk Server <your version>\Tracking。 執行下列命令： 

    ```BM UNDEPLOY ALL <drive\>:\Program Files\\<installation directory\>\BAMTracking\tracking.xml```
  
## <a name="unconfigure-btarn"></a>取消設定 BTARN
  
1.  找出並執行下列命令以取消設定 BTARN：  
  
     ***< 磁碟機\>*****: \Program Files\\< 安裝目錄\>\Configuration.exe /u**   
  
2.  在控制台中，按兩下**新增或移除程式**。  
  
3.  在**目前安裝的程式**清單中，按一下**Microsoft BizTalk Accelerator for RosettaNet**，然後按一下 **變更/移除**。  
  
4.  在**程式維護**對話方塊中，選取**移除**，然後按一下 **下一步**。  
  
5.  在**摘要**對話方塊中，按一下 **解除安裝**。  
  
6.  在**已完成解除安裝**對話方塊中，按一下 **完成**。  
  
    > [!NOTE]
    >  解除安裝程序不會移除 BTARN 資料庫 （BTARNARCHIVE、 BTARNCONFIG 和 BTARNDATA）。 您必須手動移除這些資料庫。  
  
7.  開啟**SQL Server Management Studio**。  
  
8.  在**連接到伺服器**對話方塊中，按一下 **連接**。  
  
9. 展開**資料庫**的左窗格中的節點。 其中一個 BTARN 資料庫中，以滑鼠右鍵按一下，然後按一下 **刪除**。  
  
10. 在**刪除物件**對話方塊中，選取**關閉現有的連接**，然後按一下 **確定**。  
  
