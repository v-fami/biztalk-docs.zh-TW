---
redirect_url: /biztalk/core/feature-pack-add-application-project/
redirect_document_id: True
ROBOTS: NOINDEX
title: "加入 Visual Studio Team Services 的 BizTalk Server 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2c7a1ff-0f26-45f3-9a9b-4c99a67b51a9
caps.latest.revision: "4"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 1a6b7ba32c0077b3df107b00525bb34ef011e483
ms.sourcegitcommit: a0165ec2f1e8b58545638666b7bfa2bf440036fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="add-a-biztalk-server-application-to-visual-studio-team-services"></a>加入 Visual Studio Team Services 的 BizTalk Server 應用程式
新增[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]VSTS 自動部署使用持續整合至專案。  

**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，您可自動部署應用程式，以便您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]使用 Visual Studio Team Services (VSTS) 的環境。 

本主題提供概觀，並列出部署從 Visual Studio 方案的重要步驟您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。 

## <a name="prerequisites"></a>必要條件
* 安裝[功能套件 1](https://www.microsoft.com/download/details.aspx?id=55100)上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]
* [步驟 3： 建立組建和發行定義](../core/feature-pack-add-build-release-definitions.md)
* 知識和經驗使用 Git 和 Visual Studio 中的儲存機制。 如果您是新手儲存機制和版本控制，這些可能是很好的資源： 

    [了解 Git](https://www.visualstudio.com/learn-git/)  
    [Git 和 Team Services](https://www.visualstudio.com/docs/git/overview)
* 知識和經驗的使用中的 BizTalk 專案[!INCLUDE[btsVStudioNoVersion_md](../includes/btsvstudionoversion-md.md)]

## <a name="add-biztalk-project-to-vsts"></a>將 BizTalk 專案加入至 VSTS
1. 在**Visual Studio**，連接到您**來源儲存機制**，和**複製**以您的電腦。
2. 開啟或建立**BizTalk 專案**(.btproj)。

   > [!NOTE]
   > 您可以將多個專案新增至相同的方案。
   
3. 加入新**BizTalk Server 應用程式專案**(.btaproj)。
4. 中的專案上按一下滑鼠右鍵**方案總管 中**，然後選取**屬性**。
5. 設定**版本**和連接屬性，以您**Visual Studio Team Services**帳戶。

    ![Visual Studio 組態 FP1 BizTalk](../core/media/visual-studio-configuration-fp1-biztalk.png)

6. 新增所有組件和應用程式所需的成品。
7. 更新**binding.xml**具有正確的繫結資訊檔案。
8. 更新**BizTalkServerInventory.json**成品安裝在正確的順序與所有的成品， [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。
9. 以滑鼠右鍵按一下和**建置**方案中，以便檢查是否有任何錯誤。 
10. 建置成功完成時，以滑鼠右鍵按一下您的方案，然後選取**部署**。
11. 您的應用程式應該自動部署到您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。

## <a name="see-also"></a>另請參閱
[設定此功能套件](../core/configure-the-feature-pack.md)