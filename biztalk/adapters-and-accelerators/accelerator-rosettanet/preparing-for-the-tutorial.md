---
title: "BizTalk Server 的 RosettaNet 回送教學課程的必要條件 |Microsoft 文件"
description: "若要逐步執行 RosettaNet 加速器 (BTARN)，以在 BizTalk Server 中的回送教學課程的必要條件"
caps.latest.revision: "9"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/09/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e26696c-86c5-448b-9cd6-bfd4a279151a
ms.author: mandia
ms.openlocfilehash: 9767f7823e80d4de67345ba0fbf59c1435adb8e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="prepare-for-the-tutorial"></a>準備進行教學課程

## <a name="prerequisites"></a>必要條件
再開始回送教學課程：
  
-   [安裝和設定](install-configure-biztalk-accelerator-for-rosettanet.md)快速鍵。 您可能要將 btarnhttpreceive 虛擬目錄加入至 Windows SharePoint 受管理的路徑排除清單，在 SharePoint 管理中心內。  
  
-   確定 BizTalkServerIsolatedHost 和 biztalkserverapplication 主控件有**信任的驗證**啟用選項。 若要確認，開啟 BizTalk Server 管理主控台，並展開**主機**。 以滑鼠右鍵按一下主應用程式中，選取**屬性**，並檢查**信任的驗證**如果未啟用。  

    如果您有一個以上的主控件執行個體，然後刪除所有主控件執行個體。 例如，刪除 BizTalk Server 外掛式主控的件執行個體，並保留 BizTalkServerApplication 主控件執行個體）。 這可讓您選取**信任的驗證**主機相關聯的執行個體，然後再重新建立其他主控件執行個體上。  
  
## <a name="next-step"></a>下一步
 [步驟 1： 建立主要組織](step-1-create-the-home-organization.md)