---
title: 最佳做法來管理 Certificates1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- best practices, certificates
- certificates, security
- security, certificates
- certificates, best practices
- best practices, security
- security, best practices
ms.assetid: cd182df4-0fcd-409c-9221-89f92e069f07
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e72d87530e5d080bd98ed55c2d29ca9554430375
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232086"
---
# <a name="best-practices-for-managing-certificates"></a>管理憑證的最佳作法
本節提供在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境中管理憑證的最佳作法。  
  
-   **執行環境的威脅模型分析**  
  
     執行您環境的「威脅模型分析」(TMA) 以判斷簽章或加密憑證是否有助於減輕安全性威脅。  
  
-   **與夥伴建立公開金鑰憑證的計劃**  
  
     與夥伴建立用來傳送和接收公開金鑰憑證的計劃。 如果您沒有使用簽章憑證進行合作對象解析，則可以將公用憑證附加到訊息；在此情況下，您的系統並不需要預先準備憑證的複本。  
  
-   **設定的間隔下載憑證撤銷清單**  
  
     下載憑證授權單位 (CA) 憑證撤銷的清單 (CRL) 設定的間隔。 我們建議一週下載一次。 如果 BizTalk 伺服器所加入的網域有 CA 存在，便會自動下載 CRL。  
  
-   **與協力廠商的指導方針建立提交公開金鑰**  
  
     在與夥伴的「服務等級協議」(SLA) 內容中，建立提交公開金鑰的指導方針，在他們的憑證即將到期時，以及在他們撤銷憑證時通知您。  
  
-   **驗證簽章憑證**  
  
     您務必要根據憑證撤銷清單驗證簽章憑證。 如需如何驗證簽章憑證的詳細資訊，請參閱[如何設定 MIME SMIME 解碼器管線元件](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)。  
  
-   **避免阻斷服務攻擊的數位簽章**  
  
     決定您要在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法驗證數位簽章時處理訊息的方式。 設定**驗證**接收埠上的屬性，將有助於避免阻斷服務攻擊。  
  
    > [!NOTE]
    >  **驗證-捨棄訊息**和**驗證-保留訊息**接收埠上的旗標需要正確地設定合作對象解析管線元件和合作對象為在 BizTalk Server 中定義。 如需有關如何設定合作對象解析管線元件的詳細資訊，請參閱[合作對象解析管線元件](../core/party-resolution-pipeline-component.md)。  
  
-   **建立個別的加密和未加密的訊息接收位置**  
  
     如果您打算從某些夥伴接收 MIME 加密訊息，並從其他夥伴接收未加密的訊息，請在不同的主控件中，為加密和未加密的訊息分別建立接收位置。 當您希望只有 MIME 加密訊息時，設定**允許非 MIME 訊息**解碼 MIME/SMIME 管線元件中的選項**否**。  
  
-   **與夥伴管理憑證**  
  
     將憑證管理納入夥伴管理實務的環節。 在從 BizTalk Server 環境中新增或移除合作對象時，建議您新增或移除與該夥伴相關聯的憑證。  
  
-   **移除主控件執行個體前移除憑證**  
  
     從 BizTalk Server 移除主控件執行個體前，請先移除主控件執行個體執行時所用帳戶的個人存放區中的憑證。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BizTalk Server 安全性](../core/managing-biztalk-server-security.md)   
 [管理 Windows 群組和使用者帳戶的最佳作法](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)