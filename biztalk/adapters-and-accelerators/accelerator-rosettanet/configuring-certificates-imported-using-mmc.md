---
title: 設定使用 MMC 匯入的憑證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- decryption certificates
- certificates, decryption certificates
- certificates, signing certificates
- importing certificates
- signing certificates
- certificates, importing
ms.assetid: 64dbfbcf-6026-4c68-a93a-f483ec52deac
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7663d5df833635e557af699dd5ce5fc7de9c7d9d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996119"
---
# <a name="configuring-certificates-imported-using-mmc"></a>設定使用 MMC 匯入的憑證
在匯入憑證 嵌入式管理單元使用 Microsoft Management Console (MMC) 的憑證之後，您必須設定其使用。 這包括設定 BizTalk 群組、BizTalk 主控件與外掛式主控件服務帳戶、「交易夥伴介面程序」(PIP)、交易夥伴協議與交易夥伴。 您必須執行下列步驟：  
  
> [!NOTE]
>  若您使用 CertWizard 公用程式匯入與設定憑證，則不需要手動執行這些步驟。  
  
- 設定主要組織的簽章憑證使用方式。 這意謂著您使用私密金鑰，識別外寄訊息中的主要組織。 若要如此，請設定 BizTalk 群組的簽章憑證。  
  
- 為主要組織設定解密憑證的使用方式。 請意謂著您使用交易夥伴公開金鑰對應的私密金鑰，解密內送訊息。 若要如此，請設定每個 BizTalk 主控件與 BizTalk 外掛式主控件服務帳戶的解密憑證。 您必須為主控件與外掛式主控件服務帳戶輸入相同的解密憑證，對於 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 您必須設為相同的帳戶。  
  
  > [!NOTE]
  >  BizTalk 主控件與外掛式主控件必須具有相同的解密憑證，如此才能解密相同的加密內送訊息。 執行 HTTP 配接器的 BizTalk 外掛式主控件無法存取主控件憑證，因此必須具有憑證，才能接收訊息。 BizTalk 主控件也必須具有憑證，才能在 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 接收訊息後處理訊息。  
  
- 為每個交易夥伴設定加密與簽章憑證。 若要這樣做，您必須輸入憑證**一般**索引標籤**夥伴**在 Microsoft [屬性] 頁面[!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)]([!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]) 管理主控台。 這包括加密至交易夥伴外寄訊息的公開公鑰加密憑證，以及在內送訊息中確認交易夥伴身份識別的公開金鑰簽章憑證。 如需詳細資訊，請參閱 <<c0> [ 建立或編輯夥伴](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md)。  
  
- 設定主要組織與交易夥伴之間的加密原則。 若要這樣做，您設定在交易夥伴協議**通訊協定**索引標籤**協議屬性**頁面[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]管理主控台。 如需詳細資訊，請參閱 <<c0> [ 建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)。  
  
### <a name="to-configure-the-signing-certificate-for-a-biztalk-group-or-the-decryption-certificate-for-a-biztalk-host"></a>設定 BizTalk 群組的簽章憑證或 BizTalk 主控件的解密憑證  
  
1. 按一下 **開始**，按一下**執行**，型別**runas /user:\<裝載服務\>mmc**，然後按一下 **確定**。  
  
   > [!NOTE]
   >  針對\<*裝載服務*\>，輸入您在安裝時，主控件服務關聯的服務名稱[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]。  
  
2. 輸入的密碼\<*裝載服務*\>，然後按 ENTER 鍵。  
  
3. 按一下 **開始**，指向**所有程式**，指向[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**。  
  
4. 依序展開**憑證-目前使用者**，展開**個人**，然後按一下**憑證**。  
  
5. 在右側窗格中，按兩下私用憑證。  
  
6. 在 憑證 視窗中，在**詳細資料**索引標籤上，按一下**指紋**，然後選取 顯示 視窗中的 十六進位的識別碼。 按下 CTRL+C 以複製識別碼。  
  
7. 按一下 **開始**，指向**所有程式**，指向**Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
8. 若要設定 BizTalk 群組的簽章憑證，以滑鼠右鍵按一下**Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **(Local)**，然後按一下**屬性**。 在右邊的文字方塊中按一下**指紋**，按 CTRL + V 將憑證指紋數貼到文字方塊，然後按一下**確定**。  
  
9. 若要為 BizTalk 主控件設定解密憑證，依序展開**Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **(Local)**，依序展開**主機**，以滑鼠右鍵按一下您想要的主機設定，然後再按一下**屬性**。  
  
10. 上**憑證**索引標籤上，按一下右邊的文字方塊**指紋**，按 CTRL + V 將憑證指紋數貼到文字方塊，然後按一下**確定**。  
  
    > [!NOTE]
    >  您必須設定 BizTalk 主控件 (BizTalkServerApplication) 與 BizTalk 外掛式主控件 (BizTalkServerIsolatedHost) 的解密憑證。  
  
## <a name="see-also"></a>另請參閱  
 [管理憑證](../../adapters-and-accelerators/accelerator-rosettanet/managing-certificates1.md)