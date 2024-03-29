---
title: 硬體和軟體需求的部署 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, hardware requirements
- deploying, software requirements
ms.assetid: 1dd9c4bb-b724-4195-8496-eff95cd1548a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f61a8b66f455aeffee1b5416ebb5911be61fdbec
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984655"
---
# <a name="hardware-and-software-requirements-for-deployment"></a>硬體和軟體需求的部署
下表列出的硬體與軟體建議和指定的部署架構中每個伺服器的需求。 如需有關設定必要的軟體的詳細資訊，請參閱 <<c0> [ 部署您的伺服器](../../adapters-and-accelerators/accelerator-swift/deploying-your-servers.md)。  

 所有的伺服器類型，選擇的硬碟空間、 處理器的時脈速度，並根據目前與預期的技術需求的隨機存取記憶體 (RAM) 量 (如中所述[步驟 1： 安裝基底平台](../../adapters-and-accelerators/accelerator-swift/step-1-installing-the-base-platform.md)).  


|                    [伺服器]                    |                                                                                                                                           硬體建議                                                                                                                                            |                                                                                                                                                   軟體需求                                                                                                                                                    |
|----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|             網域控制站             |                                                                                                                                             -1 的網路介面卡                                                                                                                                             |                                       Microsoft Windows Server 2012 R2 或 2012<br />Microsoft[!INCLUDE[btsAD](../../includes/btsad-md.md)]伺服器<br />網域名稱伺服器 (DNS)                                       |
|           Microsoft SQL server            | -2 個網路介面卡<br />選擇性： 存放區域網路 (SAN) 磁碟中，選擇 平均輸送量尖峰輸送量，輸送量尖峰時間，加上所需的硬碟空間的平均訊息大小。 SAN 應該分割成三個磁碟機： 資料、 交易記錄和仲裁。 |                                                                        Microsoft Windows Server 2012 R2 或 2012<br />-   [!INCLUDE[SQLServer2008or2005](../../includes/sqlserver2008or2005-md.md)]                                                                         |
|       訊息的 BizTalk server        |                                                                                                                                            -2 個網路介面卡                                                                                                                                             |                                                  Microsoft Windows Server 2012 R2 或 2012<br />BizTalk Server<br />-   [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]                                                   |
| BizTalk HTTP 前端伺服器 （MRSR 站台） |                                                                                                                                            -2 個網路介面卡                                                                                                                                             | Microsoft Windows Server 2012 R2 或 2012<br />為 Internet Information Services (IIS)<br />啟用路由的訊息佇列服務<br />BizTalk Server<br />-   [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] |
|     協調流程的 BizTalk server     |                                                                                                                                             -1 的網路介面卡                                                                                                                                             |                                                  Microsoft Windows Server 2012 R2 或 2012<br />BizTalk Server<br />-   [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]                                                   |

