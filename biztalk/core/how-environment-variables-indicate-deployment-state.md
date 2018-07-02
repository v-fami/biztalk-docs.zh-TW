---
title: 環境變數如何指示部署狀態 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scripts, variables
ms.assetid: 022b782b-008d-41a7-9880-d1c4e5e4015e
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d21baa6ef6e6d82fc179497b4993cf3af6fb1a5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983983"
---
# <a name="how-environment-variables-indicate-deployment-state"></a>環境變數如何指示部署狀態
前置或後置處理指令碼一旦被叫用，便會檢查環境變數 BTAD_ChangeRequestAction、BTAD_InstallMode 與 BTAD_HostClass 以判斷目前所處的部署狀態 (安裝、匯入、刪除、解除安裝、匯入回復，或者安裝回復)。  

 下表描述三個指示不同部署狀態之變數的組合。  


|       部署狀態        |     預期值      |
|-------------------------------|--------------------------|
|                               | BTAD_ChangeRequestAction |
| 不使用覆寫旗標匯入 |          建立          |
|  使用覆寫旗標匯入   |          Update          |
|            安裝            |          Update          |
|           Uninstall           |          DELETE          |
|        匯入回復        |          DELETE          |
|       安裝回復        |          DELETE          |

## <a name="see-also"></a>另請參閱  
 [使用前置和後置處理指令碼自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)   
 [BTAD_ChangeRequestAction](../core/btad-changerequestaction.md)   
 [BTAD_InstallMode](../core/btad-installmode.md)   
 [BTAD_HostClass](../core/btad-hostclass.md)