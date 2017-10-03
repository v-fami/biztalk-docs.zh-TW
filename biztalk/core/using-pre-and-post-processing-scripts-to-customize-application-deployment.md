---
title: "使用前置和後置處理指令碼自訂應用程式部署 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- customizing, applications
- applications, customizing
- scripts, applications
- scripts, customizing
ms.assetid: 47627394-d594-491b-9098-38c5d028a378
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7dc0afd7ed042f475a9a008125c968f401e6df92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-pre--and-post-processing-scripts-to-customize-application-deployment"></a>使用前置和後置處理指令碼自訂應用程式部署
本節中的主題描述如何建立前置或後置處理指令碼，以便在匯入、安裝或解除安裝應用程式時執行動作。 前置處理指令碼會在應用程式匯入或安裝開始前，以及在解除安裝完成後，執行一項動作或一組動作。 後置處理指令碼會在應用程式匯入或安裝完成後，或在解除安裝開始前，執行一項動作或一組動作。  
  
 例如，您可能想要包含會在安裝前執行的前置處理指令碼，以便在安裝期間覆寫資源檔以前，備份這些資源檔。 或者您可能想要執行後置處理指令碼，在安裝應用程式後將憑證新增到憑證存放區。  
  
> [!NOTE]
>  BizTalk Server 包括範例前置和後置處理指令碼。 使用範例指令碼的相關資訊，請參閱[範本 （應用程式部署範例）](../core/template-application-deployment-sample.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [建立前置或後置處理指令碼](../core/creating-a-pre-or-post-processing-script.md)  
  
-   [環境變數如何指示部署狀態](../core/how-environment-variables-indicate-deployment-state.md)  
  
-   [在部署期間檔案成品的狀態](../core/status-of-file-artifacts-during-deployment.md)  
  
-   [前置和後置處理指令碼環境變數](../core/pre-and-post-processing-script-environment-variables.md)