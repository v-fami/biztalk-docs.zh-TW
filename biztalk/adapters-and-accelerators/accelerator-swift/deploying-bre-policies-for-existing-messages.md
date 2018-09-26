---
title: BRE 原則部署的現有訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 585c903d-ee44-4e92-8798-febb176367e3
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4cd094feabe1ba23a6a73c89aae3a1042b8f7fc9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965004"
---
# <a name="deploying-bre-policies-for-existing-messages"></a>將 BRE 原則部署現有的訊息
**若要部署的相關的商務規則：**  
  
1.  按一下**啟動**，按一下 **程式**，按一下  **Microsoft BizTalk Accelerator for SWIFT**，然後按一下  **BRE 部署公用程式**。  
  
2.  在 BRE 部署公用程式，按一下 **瀏覽**。  
  
3.  在.NET 全域組件快取] 對話方塊中，選取**SWIFT MX 結構描述**，然後按一下 [**確定**。  
  
4.  按一下**部署**。  
  
     根據部署與該組件的結構描述，部署公用程式會識別相關的規則，並將其發行 BRE 搭配使用。 完成時，BRE 部署公用程式會顯示下列訊息: 「 已完成部署。 檢視記錄檔或商務規則編輯器 」 以取得詳細資料。 」  
  
5.  關閉 SWIFT BRE 部署公用程式的對話方塊。  
  
6.  在 Windows 檔案總管，瀏覽至*\<磁碟機\>*: \Documents and Settings\All Users\Application 資料，確認記錄檔 BREDeploymentLog.txt 顯示資料夾中。  
  
7.  按一下**啟動**，按一下 **執行**，型別**services.msc**，然後按一下 **確定**。 在 服務 （本機） 視窗中，以滑鼠右鍵按一下**規則引擎更新服務**，然後按一下 **重新啟動**。