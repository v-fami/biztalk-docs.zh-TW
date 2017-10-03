---
title: "安裝 「 解析程式服務 」 範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fce9bbeb-9377-41af-8ca7-740ce4d1f617
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b06c7383dee805612a3f599148f1d631891ace79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="installing-the-resolver-service-sample"></a>安裝 「 解析程式服務 」 範例
本章節描述解析程式服務範例的安裝程序。 解析程式服務依存於[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]核心方案。 安裝[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]核心自動複製並安裝到正確的位置，此範例所需的核心組件。  
  
 **若要從方案專案安裝解析程式服務範例**  
  
1.  在 Windows 檔案總管 中，開啟 \Source\Samples\ResolverService\Install\Scripts 資料夾。  
  
2.  按兩下 Setup_bin.cmd 檔案。  
  
3.  若要確認成功安裝範例的一部分，或如果您執行應用程式時遇到問題，您可以使用下表中所提供的清單來檢查是否有必要的組件和其他成品。  
  
|位置|類別目錄|名稱和版本的元件|  
|--------------|--------------|---------------------------------------|  
|BizTalk 應用程式 GlobalBank.ESB|協調流程|(無)|  
|BizTalk 應用程式 GlobalBank.ESB|傳送埠|(無)|  
|BizTalk 應用程式 GlobalBank.ESB|接收埠|(無)|  
|BizTalk 應用程式 GlobalBank.ESB|接收位置|(無)|  
|BizTalk 應用程式 GlobalBank.ESB|結構描述|(無)|  
|BizTalk 應用程式 GlobalBank.ESB|管線|(無)|  
|BizTalk 應用程式 GlobalBank.ESB|資源|(無)|  
|BizTalk 應用程式 GlobalBank.ESB|原則|ResolveEndpoint|  
|||ResolveMap|  
|BizTalk 應用程式 GlobalBank.ESB|地圖|(無)|  
|全域組件快取|組件|(無)|  
|%Program Files %\\[!INCLUDE[prague](../includes/prague-md.md)]\Pipeline 元件|管線元件|(無)|