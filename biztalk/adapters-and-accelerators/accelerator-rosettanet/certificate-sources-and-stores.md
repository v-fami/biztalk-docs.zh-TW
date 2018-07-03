---
title: 憑證來源與存放區 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates, certificate storage
- importing certificates
- certificates, certificate sources
- certificates, importing
ms.assetid: 3e98fb56-4368-46f3-9329-c44fed11f4fb
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13272f66fca9faec099d8fe8f1b6fb69bb1e6660
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990335"
---
# <a name="certificate-sources-and-stores"></a>憑證來源與存放區
本主題描述從何處匯入憑證，以及在何處存放憑證。  
  
## <a name="certificate-sources"></a>憑證來源  
 您可以從下列檔案匯入憑證：  
  
- .pfx 或 .p12 檔案中的私用憑證。 匯入憑證之後，安全地存放這些檔案。 如果您使用 CertWizard 公用程式的私用憑證匯入，您可以設定 **/exportable**切換至`False`，這是預設設定，以便私用憑證無法從存放區匯出到檔案。 如果您設定 **/exportable**切換至`True`，您可以將這些憑證匯出至檔案從憑證 Microsoft Management Console (MMC)。  
  
- .cer 或 .der 檔案中的公開憑證。 交易夥伴會將憑證放在這些檔案中傳送給您。  
  
- .cer 或 .der 檔案中的根憑證。 憑證授權單位會將根憑證放在這些檔案中傳送給您。  
  
## <a name="certificate-storage"></a>憑證存放區  
 您可以將憑證匯入本機電腦上兩個「憑證」存放區之一。 中的公開憑證存放**Certificates (Local Computer)** 儲存。 您可以開啟此存放區的節點，開啟**Certificates (Local Computer)** 節點，在 Microsoft [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] ([!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]) 管理主控台。 您可以存取**Certificates (Local Computer)** 儲存如果您的電腦上具有系統管理權限。 將公開憑證存放在下列資料夾：  
  
- 主要的個人資料夾中的公開憑證**Certificates (Local Computer)** 儲存  
  
- 交易夥伴的其他人資料夾中的公開憑證**Certificates (Local Computer)** 儲存  
  
- 從憑證授權單位的受信任的根憑證授權單位資料夾中的憑證**Certificates (Local Computer)** 儲存  
  
  儲存在私用憑證**憑證-目前使用者**儲存。 您可以開啟此存放區的節點，開啟管理主控台中使用**runas**命令與主控件服務帳戶的使用者。 如需詳細資訊，請參閱 <<c0> [ 匯入憑證](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CertWizard 公用程式匯入憑證](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-the-certwizard-utility.md)   
 [使用 MMC 匯入憑證](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-mmc.md)   
 [匯入憑證&#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/certificate-sources-and-stores.md)