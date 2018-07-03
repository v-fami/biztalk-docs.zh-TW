---
title: 安裝憑證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates, installing
- installing, certificates
ms.assetid: 7525f771-623c-420f-99ca-c834e819829d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 111bd267bc7d0bc12d582c3b74846b8874ed8b4d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012543"
---
# <a name="installing-certificates"></a>安裝憑證
若要傳送、 修復或提交訊息，您必須安裝適當的認證。 本主題描述如何新增憑證。 在生產環境中，請參閱您的 IT 部門的憑證。  

 **摘要**  

 本節說明如何建立並儲存下列憑證：  

- 每個用戶端電腦上將 Message Repair 和 New Submission 角色憑證-目前使用者的個人資料夾中的每個憑證存放區  

- 每個 BizTalk 協調流程伺服器電腦上將 Message Repair 和 New Submission 角色的憑證 （本機電腦） 的其他人 資料夾中的每個憑證存放區  

- 憑證授權單位憑證在每個用戶端電腦上的 Certificates (Local Computer) 存放區中的 [受信任的根憑證授權單位] 資料夾  

  如果您已部署[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]的單一電腦上，也可以安裝在同一部電腦上的憑證伺服器，您需要從受管理的路徑排除憑證伺服器，適用於 Microsoft SharePoint Server。  

  此部分包含：  

- [將憑證新增至用戶端上的憑證存放區](../../adapters-and-accelerators/accelerator-swift/adding-certificates-to-the-certificates-store-on-the-client.md)  

- [將憑證新增至伺服器上的憑證存放區](../../adapters-and-accelerators/accelerator-swift/adding-certificates-to-the-certificates-store-on-the-server.md)  

- [從單一電腦部署的受管理路徑中排除 CertSrv](../../adapters-and-accelerators/accelerator-swift/excluding-certsrv-from-managed-paths-on-a-single-computer-deployment.md)
