---
title: 在部署期間檔案成品的狀態 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- artifacts, status
- deploying [artifacts], status
ms.assetid: 6d0f7336-c2cb-4aa4-9f1d-55fb85fe78bf
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1f57716741bb61c7a9f6f012aed14ec04c8e250
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="status-of-file-artifacts-during-deployment"></a>部署期間檔案成品的狀態
在執行前置或後置處理指令碼時，您可能需要知道在檔案系統上有哪些以檔案為基礎的成品。 例如，您可能想要讓後置處理指令碼在解除安裝期間執行，並且要它從檔案系統刪除特定成品檔案。 以檔案為基礎的成品，除了在 BizTalk 資料庫有其表示之外，在本機檔案系統上也有其檔案。 以檔案為基礎的成品範例包括 COM 元件、.NET 組件、BizTalk 組件、BAM 成品、臨機操作檔案、指令碼和繫結檔案。  
  
 下表摘要說明部署程序期間每個時間點的成品檔案狀態。  
  
|部署程序時間點|應用程式成品檔案的狀態|  
|-------------------------------------|------------------------------------------|  
|安裝前|本機檔案系統上只有 System.BizTalk.File 型別的檔案。*|  
|安裝後|本機檔案系統上有所有的檔案。*|  
|解除安裝前|本機檔案系統上有所有的檔案。*|  
|解除安裝後|已從本機檔案系統刪除所有檔案。|  
|匯入前|本機檔案系統上沒有檔案，除非在本機電腦上安裝應用程式。|  
|匯入後|本機檔案系統上沒有檔案，除非在本機電腦上安裝應用程式。|  
  
 \* 本機檔案系統上的檔案存在，只有當將檔案加入至應用程式時，已指定有效的目的地位置。  
  
## <a name="see-also"></a>另請參閱  
 [使用前置和後置處理指令碼自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)