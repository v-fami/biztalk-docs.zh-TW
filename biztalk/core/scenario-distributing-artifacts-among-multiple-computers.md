---
title: 案例： 分配給多部電腦間的成品 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying [artifacts], multiple computers
- examples, distributing
- examples, artifacts
- artifacts, distributing
- artifacts, examples
- deploying [artifacts], examples
- examples, deploying
ms.assetid: 7000cded-1fda-4276-b7f3-3f427f686f64
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abedc60ad13c7e8b2be3ce4caa7b8d34262b4e5c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269158"
---
# <a name="scenario-distributing-artifacts-among-multiple-computers"></a>案例： 分配給多部電腦間的成品
本主題說明如何將應用程式中的成品選擇性安裝在不同電腦的應用程式部署案例。 如果您要應用程式中的特定組件或其他類型的成品只安裝在 BizTalk 群組中的特定電腦上，可以這樣做。 若要執行這項作業，您可以根據要一起安裝在實體電腦上的成品，將應用程式中包含的成品匯出至多個 .msi 檔案。  
  
 下圖顯示 BizTalk 群組 1 匯入至 BizTalk 管理資料庫的.msi 檔案。 這會建立訂單處理應用程式和其所有的成品，該群組中。 接著將應用程式成品匯出至兩個不同的 .msi 檔案。 其中一個 .msi 檔案包含 Assembly1、Certificate1 和 Script1。 另一個 .msi 檔案包含 Assembly2、Script2 和 VirtualDirectory1。  
  
 這兩個.msi 檔案匯入 BizTalk 群組 2。 因為它們都屬於訂單處理應用程式時，所有的這兩個.msi 檔案中的成品會匯入新的群組中名為訂單處理相同的應用程式。  
  
 此外，應用程式成品會從 .msi 檔案安裝在群組中將執行這些成品的電腦上。 請注意，包含虛擬目錄的 .msi 檔案會安裝在 BizTalk Server B 和 BizTalk Server C，這兩個伺服器都是執行 IIS。  
  
 ![安裝在不同電腦上的成品](../core/media/distributionofartifacts.gif "DistributionOfArtifacts")  
  
## <a name="see-also"></a>另請參閱  
 [應用程式部署和管理案例](../core/application-deployment-and-management-scenarios.md)   
 [如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)   
 [如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)   
 [如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)