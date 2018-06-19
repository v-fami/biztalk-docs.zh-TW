---
title: 安裝和設定 BizTalk Accelerator for SWIFT HTTP 前端伺服器上 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HTTP server, installing BizTalk Accelerator for SWIFT
- BizTalk Accelerator for SWIFT, installing on HTTP server
ms.assetid: 1deaa5f7-9da2-4d4b-8367-2d6900065839
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8a63277ec58981f5f0f904aabe61957de66df08
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965668"
---
# <a name="installing-and-configuring-biztalk-accelerator-for-swift-on-http-front-end-servers"></a>安裝和設定 BizTalk Accelerator for SWIFT HTTP 前端伺服器上
本章節描述如何安裝及設定[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]HTTP 前端伺服器上。 這些伺服器主要用於通訊的 SWIFT 網路。  
  
### <a name="to-install-and-configure-biztalk-accelerator-for-swift-on-the-http-front-end-server"></a>若要在安裝及設定 BizTalk Accelerator for SWIFT HTTP 前端伺服器  
  
1.  執行自訂安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]。 安裝**MRSR**和**Web 元件 Message Repair 和 New Submission**功能。  
  
    > [!NOTE]
    >  安裝完成後，「 組態精靈 」 會啟動。  
  
2.  在 Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]組態主控台中，設定**MCRR**和**WebService**。  
  
3.  組態精靈的 網頁伺服器上完成後，請在資料夾中開啟 web.config 檔案\<*磁碟機*\>: \Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]\Service\ [記事本] 中的。 搜尋 「 授權 」。 在**授權**區段中，將角色值設定為 A4SWIFT users 群組的名稱。