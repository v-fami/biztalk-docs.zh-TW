---
title: "環境變數如何指示部署狀態 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: scripts, variables
ms.assetid: 022b782b-008d-41a7-9880-d1c4e5e4015e
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 041e77eadb7c1b62e3441ee3b3c138203299f3a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-environment-variables-indicate-deployment-state"></a>環境變數如何指示部署狀態
前置或後置處理指令碼一旦被叫用，便會檢查環境變數 BTAD_ChangeRequestAction、BTAD_InstallMode 與 BTAD_HostClass 以判斷目前所處的部署狀態 (安裝、匯入、刪除、解除安裝、匯入回復，或者安裝回復)。  
  
 下表描述三個指示不同部署狀態之變數的組合。  
  
|部署狀態|預期值|  
|----------------------|---------------------|  
||BTAD_ChangeRequestAction|BTAD_InstallMode|BTAD_HostClass|  
|不使用覆寫旗標匯入|建立|匯入|ConfigurationDb|  
|使用覆寫旗標匯入|Update|匯入|ConfigurationDb|  
|Install|Update|Install|BizTalkHostInstance|  
|Uninstall|Delete|Uninstall|BizTalkHostInstance|  
|匯入回復|Delete|匯入|ConfigurationDb|  
|安裝回復|Delete|Install|BizTalkHostInstance|  
  
## <a name="see-also"></a>另請參閱  
 [使用前置和後置處理指令碼自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)   
 [BTAD_ChangeRequestAction](../core/btad-changerequestaction.md)   
 [BTAD_InstallMode](../core/btad-installmode.md)   
 [BTAD_HostClass](../core/btad-hostclass.md)