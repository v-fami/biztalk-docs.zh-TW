---
title: "匯出憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exporting certificates
- certificates, exporting
ms.assetid: edeeb300-19d6-44a8-b730-dcd15891cdf9
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1898162b27956e4e527013ff765edf6aea440e9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="exporting-certificates"></a>匯出憑證
本主題描述如何使用「憑證匯出精靈」來匯出憑證。 使用此精靈可以匯出公開憑證或私用憑證。  
  
### <a name="to-export-a-partner-certificate"></a>匯出交易夥伴憑證  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] ，然後按一下 [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **管理主控台**.  
  
2.  展開**憑證 （本機電腦）**，依序展開**其他人**，然後按一下**憑證**。  
  
3.  在右窗格中，以滑鼠右鍵按一下憑證名稱，指向**所有工作**，然後按一下**匯出**。  
  
4.  在**歡迎使用 憑證匯出精靈**頁面上，按一下**下一步**。  
  
5.  在**匯出檔案格式**頁面上，選取您想要使用之檔案的格式。 此格式通常是 DER 編碼的二進位 x.509 (可匯出二進位編碼的檔案) 或 Base-64 編碼的 x.509 (可匯出 Base-64 編碼的檔案)。  
  
    > [!NOTE]
    >  以 Base-64 將憑證編碼可讓您使用 UNIX 伺服器上的憑證。  
  
6.  在**要匯出的檔案**頁面上，按一下**瀏覽**，找出您想要儲存檔案，輸入檔案的名稱，按一下 **下一步**，然後按一下**完成**.  
  
### <a name="to-export-the-home-organization-certificate"></a>匯出主要組織憑證  
  
1.  按一下**啟動**，按一下 **執行**，型別**runas /user:\<裝載服務 > mmc**，其中\< *hostservice*> 是您在安裝時，主控件服務關聯的服務名稱[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]，然後按一下**確定**執行[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]Management Console (MMC) 的內容中主機服務。  
  
    > [!NOTE]
    >  在您執行**runas**命令，以取得服務主機，其為存取主要組織憑證所需的身份識別。  
  
2.  展開**憑證-目前使用者**，依序展開**個人**，然後按一下**憑證**。  
  
3.  在右窗格中，以滑鼠右鍵按一下憑證名稱，指向**所有工作**，然後按一下**匯出**。  
  
4.  在**歡迎使用 憑證匯出精靈**頁面上，按一下**下一步**。  
  
5.  若要匯出憑證的私用的索引鍵相關聯的公開金鑰，將保留**否，不要匯出私密金鑰**選取。 若要匯出的私密金鑰，請選取**是，匯出私密金鑰**。  
  
    > [!NOTE]
    >  如果您選取**是，匯出私密金鑰**，強烈建議您不要傳送產生的檔案給夥伴。  
  
    > [!NOTE]
    >  **是，匯出私密金鑰**選項將無法使用，如果您未進行私密金鑰可匯出當您第一次匯入。  
  
6.  在**匯出檔案格式**頁面上，選取您想要使用之檔案的格式。 此格式通常是 DER 編碼的二進位 x.509 (可匯出二進位編碼的檔案) 或 Base-64 編碼的 x.509 (可匯出 Base-64 編碼的檔案)。  
  
    > [!NOTE]
    >  以 Base-64 將憑證編碼可讓您使用 UNIX 伺服器上的憑證。  
  
7.  在**要匯出的檔案**頁面上，按一下**瀏覽**，找出您想要儲存檔案，輸入檔案的名稱，按一下 **下一步**，然後按一下**完成**.  
  
## <a name="see-also"></a>另請參閱  
 [管理憑證](../../adapters-and-accelerators/accelerator-rosettanet/managing-certificates1.md)