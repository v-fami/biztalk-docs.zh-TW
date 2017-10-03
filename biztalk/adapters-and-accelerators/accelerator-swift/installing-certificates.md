---
title: "安裝憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, installing
- installing, certificates
ms.assetid: 7525f771-623c-420f-99ca-c834e819829d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5ded26548303dfe9c9a095c24396b4e2683ca4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="installing-certificates"></a>安裝憑證
若要傳送、 修復或提交訊息，您必須安裝適當的認證。 本主題描述如何加入憑證。 在實際執行環境中，請參閱您 IT 部門以取得憑證。  
  
 **摘要**  
  
 本節提供有關如何建立及儲存下列憑證的指示：  
  
-   每個用戶端電腦上的每個訊息修復和新送出憑證-目前使用者的個人資料夾中的角色的憑證存放區  
  
-   每個 BizTalk 協調流程伺服器電腦上的每個訊息修復和新送出憑證 （本機電腦） 的其他人資料夾中的角色的憑證存放區  
  
-   憑證授權單位的憑證到信任的根憑證授權單位資料夾中每個用戶端電腦上的憑證 （本機電腦） 存放區  
  
 如果您已部署[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]的單一電腦上，也有相同的電腦上安裝的憑證伺服器，您要排除的受管理的路徑中的憑證伺服器[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]SharePoint 伺服器。  
  
 此部分包含：  
  
-   [將憑證新增至用戶端的憑證存放區](../../adapters-and-accelerators/accelerator-swift/adding-certificates-to-the-certificates-store-on-the-client.md)  
  
-   [將憑證新增到伺服器的憑證存放區](../../adapters-and-accelerators/accelerator-swift/adding-certificates-to-the-certificates-store-on-the-server.md)  
  
-   [從單一電腦部署受管理的路徑排除 CertSrv](../../adapters-and-accelerators/accelerator-swift/excluding-certsrv-from-managed-paths-on-a-single-computer-deployment.md)