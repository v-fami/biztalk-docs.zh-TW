---
title: 準備部署 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, planning
ms.assetid: 437caa31-f7f8-42e0-af1f-13aaee0955cd
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d7b6f0677b542ad03b2109eddb3352924f6b59c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966495"
---
# <a name="preparing-for-deployment"></a>準備部署
本節提供部署的規劃和準備階段的相關資訊。 實作部署之前做好下列準備：  
  
1. 閱讀並了解任何已知的問題，然後準備設備：  
  
   -   建立一份執行的硬體和軟體所需的部署，並反映您的部署 （根據網路圖表並針對您所選取的部署架構） 的變化的網路圖表] 和 [部署工作表。  
  
   -   取得的硬體和軟體，在您的檢查清單。 此擷取包含所有的 service pack、 hotfix 與您的部署所需的軟體更新下載。  
  
        下載使用的電腦具有網際網路存取這些軟體元件，並複製到 CD-ROM 更容易散發這些軟體元件。  
  
2. 分隔成不同的階段部署，並識別每個階段相關聯的工作。 這項策略可簡化部署程序，藉由組織依據特定部署階段的工作。 例如，指定的部署包含下列伺服器部署階段：  
  
3. 設定網域控制站。  
  
4. 設定資料庫 (包括執行階段[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]叢集和設計階段的資料庫伺服器)。  
  
5. 設定 BizTalk 伺服器。  
  
   此部分包含：  
  
-   [網路需求](../../adapters-and-accelerators/accelerator-swift/network-requirements.md)  
  
-   [部署的硬體和軟體需求](../../adapters-and-accelerators/accelerator-swift/hardware-and-software-requirements-for-deployment.md)