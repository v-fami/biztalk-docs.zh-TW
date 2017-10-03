---
title: "匯入憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing certificates
- certificates, importing
ms.assetid: c2576f89-b5de-4250-9c54-74c8a218bb39
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c78773d6eb1fc7e51ca80afadfd282d54def80b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="importing-certificates"></a>匯入憑證
本節描述如何匯入憑證，其中包括從何處匯入憑證、將憑證存放在何處，以及匯入憑證的工具。  
  
 有兩種匯入憑證的方法。 您可以使用 CertWizard 工具，或 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC) 的「憑證」嵌入式管理單元。  
  
-   CertWizard 為逐步執行命令列精靈，可根據參數的設定來設定憑證的使用方式。 此工具會提供在[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK 資料夾。  
  
-   您可以利用 MMC 中的「憑證」嵌入式管理單元，將憑證匯入至憑證存放區。 不過，此手動程序會要求您必須個別設定憑證的使用方式。  
  
    > [!IMPORTANT]
    >  若要在 MMC 中匯入或使用私用憑證，登入的使用者必須具有 BizTalk 主控件的使用者身份識別。 如果沒有，您必須執行**runas**命令搭配使用者參數和主控件服務帳戶，以啟動 憑證 MMC，例如**runas /user:hostsvc mmc**。 執行此命令之後，便會取得 BizTalk 主控件 (BizTalkServerApplication 與 BizTalkServerIsolatedHost) 的使用者身份識別。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [憑證來源與存放區](../../adapters-and-accelerators/accelerator-rosettanet/certificate-sources-and-stores.md)  
  
-   [使用 CertWizard 公用程式匯入憑證](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-the-certwizard-utility.md)  
  
-   [使用 MMC 匯入憑證](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-mmc.md)