---
title: 安裝和設定 BizTalk Accelerator for SWIFT HTTP 前端伺服器上 |Microsoft Docs
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
ms.openlocfilehash: 375f5f26c9c71554f4ad44bd688f1d715cb81b92
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973455"
---
# <a name="installing-and-configuring-biztalk-accelerator-for-swift-on-http-front-end-servers"></a>安裝和設定 BizTalk Accelerator for SWIFT HTTP 前端伺服器上
本章節描述如何安裝和設定[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]HTTP 前端伺服器上。 這些伺服器是主要用來與 SWIFT 網路通訊。  

### <a name="to-install-and-configure-biztalk-accelerator-for-swift-on-the-http-front-end-server"></a>安裝和設定 BizTalk Accelerator for SWIFT，HTTP 前端伺服器上  

1. 執行自訂安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]。 安裝**MRSR**並**Message Repair 和 New Submission 的 Web 元件**功能。  

   > [!NOTE]
   >  安裝完成後，便會啟動 [組態精靈]。  

2. 在 Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]組態主控台中，設定**MCRR**並**WebService**。  

3. 完成組態精靈的 網頁伺服器上之後，請在資料夾中開啟 web.config 檔案\<*磁碟機*\>: \Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]\Service\ 在記事本中的。 搜尋 「 授權 」。 在 **授權**區段中，將角色值設 A4SWIFT 使用者群組的名稱。
