---
title: 如何設定 ENTSSO MA 的 MIIS |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c7820384-ff64-4628-9e35-02b13803928f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 969a52beb02c3d2ba237369c16efec9ee84e2ef1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248134"
---
# <a name="how-to-configure-miis-for-entsso-ma"></a>如何設定 ENTSSO MA 的 MIIS
當您在執行 Microsoft Identity Integration Server (MIIS) 的電腦上安裝企業單一登入 (SSO) 管理功能 (完整版本或僅限管理版本) 時，ENTSSO 管理代理程式也會自動安裝 。 這表示當您開啟 MIIS 時，幾乎所有組態都已經設定完成。 唯一缺少的部分是連線資訊。  
  
 開始此程序之前，請先確定備妥下列資訊：  
  
-   ENTSSO 伺服器名稱。  
  
-   ENTSSO 管理代理程式用來與 SSO 伺服器通訊的 Windows 帳戶使用者識別碼和密碼。  
  
### <a name="to-configure-the-management-agent-within-miis"></a>若要在 MIIS 中設定管理代理程式  
  
1.  開啟 MIIS，然後開啟**Identity Manager**。  
  
2.  開啟**建立管理代理程式** 對話方塊。  
  
3.  選取**企業單一登入**清單中。  
  
     這會啟動**建立管理代理程式精靈**。  
  
4.  在**設定連線資訊**頁面上，於**連接到：** 欄位中，輸入 SSO 伺服器的名稱。  
  
5.  輸入 ENTSSO 管理代理程式的名稱。 這個名稱必須與 ENTSSO.xml 檔案中指定的名稱相符。  
  
6.  在**使用者**欄位中，指定 ENTSSO 管理代理程式會使用來管理 SSO 資料庫中的對應的網域帳戶。  
  
     這個帳戶必須是 SSO 系統中 SSO 分支機構系統管理員或 SSO 系統管理員帳戶的成員。  
  
7.  在**密碼**欄位中，輸入該使用者的密碼。  
  
8.  按一下**下一步**，接受預設值，直到您到達**設定延伸模組**頁面。  
  
9. 接近**連接資訊**密碼延伸模組中，按一下 **設定**。  
  
     **連線設定** 對話方塊隨即出現。  
  
10. 在**連接到**方塊中，輸入適當的帳戶。 這個帳戶必須與所指定電腦上執行之 ENTSSO 服務的服務帳戶相同。  
  
11. 在**使用者**和**密碼**欄位中，輸入使用者名稱和密碼的帳戶。  
  
12. 按一下 **[確定]**。  
  
13. 在**MIISCreate 管理代理程式**，按一下 **完成**。  
  
14. 在**Identity Manager**，按一下 **工具**功能表，然後再按一下**選項**。  
  
     **選項** 對話方塊隨即出現。  
  
15. 選取**啟用 metaverse 規則延伸模組**。  
  
16. 在**規則延伸模組名稱 欄位**，輸入**Microsoft.EnterpriseSingleSignOn.ManagementAgent.dll**。  
  
17. 按一下**確定**，關閉 MIIS。  
  
## <a name="see-also"></a>另請參閱  
 [如何使用 ENTSSO 管理代理程式](../core/how-to-use-the-entsso-management-agent.md)