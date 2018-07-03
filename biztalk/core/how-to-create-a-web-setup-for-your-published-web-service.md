---
title: 如何建立 Web 安裝程式已發佈的 Web 服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, Web services
- Web services, deploying
- Web services, installing
- Web services, .msi file
- .msi files, Web services
ms.assetid: 77c86242-1d27-4d99-ae00-fe2614bc13ef
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d894cba37b85c4f18fe2a05af33eb2f4e6e1981e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984383"
---
# <a name="how-to-create-a-web-setup-for-your-published-web-service"></a>如何為所發佈的 Web 服務建立 Web 安裝
您可以建立安裝套件，以便在實際執行環境中安裝您的 Web 服務。 這個作業會建立 .MSI 檔案。  
  
### <a name="to-create-an-installation-package-to-produce-an-msi-file-using-visual-studio"></a>若要建立安裝套件，以產生。使用 Visual Studio 的 MSI 檔案  
  
1. 開啟您已發佈的 ASP.NET Web 服務專案。  
  
2. 在 [方案總管] 中，以滑鼠右鍵按一下方案節點，請按一下**新增**，然後按一下**新的專案**。  
  
3. 在 **加入新的專案**對話方塊的 **專案類型**區域中，展開**其他專案類型**，展開**安裝和部署專案**，然後選取**Visual Studio 安裝程式**。 在 **範本**區域中，選取**Web 安裝專案**。  
  
4. 在 **名稱**文字方塊中，輸入 Web 安裝專案的名稱。 您可以使用相同的名稱為 ASP.NET Web 服務專案並加入"_Setup"做為尾碼，然後按**確定**。  
  
5. 在方案總管 中，請以滑鼠右鍵按一下新建立的 Web 安裝專案節點，並指向**檢視**，然後按一下**檔案系統**。  
  
6. 在 **檔案系統** 視窗中，以滑鼠右鍵按一下**Web 應用程式資料夾**節點並指向**新增**，然後按一下 **專案輸出**。  
  
7. 在 **加入專案輸出群組**對話方塊方塊中，選取**主要輸出**並**內容檔案**從 ASP.NET Web 服務專案，然後按一下**確定**.  
  
8. 在 [方案總管] 中，展開**偵測到的相依性**Web 安裝專案下的節點。  
  
9. 選取所有相依性。 在 **屬性**視窗中，將**排除**屬性設 **，則為 True**。  
  
10. 建置您的 Web 安裝專案。  
  
    > [!NOTE]
    >  建立 Web 安裝專案的詳細資訊，請參閱 「 如何建立或加入 Web 安裝程式專案 」，在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]說明的集合，在[ http://go.microsoft.com/fwlink/?LinkId=62268 ](http://go.microsoft.com/fwlink/?LinkId=62268)。  
  
## <a name="see-also"></a>另請參閱  
 [在非 Visual Studio 電腦上部署已發佈 Web 服務](../core/deploying-published-web-services-on-a-non-visual-studio-computer.md)