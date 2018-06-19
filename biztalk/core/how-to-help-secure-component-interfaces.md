---
title: 如何協助保護元件介面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- component interfaces, helping to secure
- security, component interfaces
ms.assetid: 03b2af44-78e7-4fdc-bfa3-7697b2a60986
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54136aaeae9578ae4e438c5bd8b95b902d618f96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255214"
---
# <a name="how-to-help-secure-component-interfaces"></a>如何協助保護元件介面的安全
在您開始測試元件介面之前，必須先設定其安全性。 下列程序描述如何設定 PeopleSoft 8.4 版，元件介面安全性，但您可以針對 8.1 版使用此程序。  
  
### <a name="to-configure-interface-security"></a>若要設定介面安全性  
  
1.  展開**PeopleTools**，依序展開**安全性**，依序展開**使用者設定檔**，然後展開**Permissions & Roles**。  
  
     ![](../core/media/psadapter-47-ps-configsecurity1.gif "PSAdapter_47_PS_ConfigSecurity1")  
  
2.  按一下**權限清單**。  
  
3.  按一下 **[搜尋]**。  
  
     ![](../core/media/psadapter-48-ps-configsecurity2.gif "PSAdapter_48_PS_ConfigSecurity2")  
  
4.  在**Permission Lists Search**  窗格中，選取相關的權限清單。  
  
     此時就會顯示下列視窗。  
  
     ![](../core/media/psadapter-49-ps-configsecurity3.gif "PSAdapter_49_PS_ConfigSecurity3")  
  
5.  按一下向右箭號旁**sign-on Times**索引標籤，顯示多個索引標籤。  
  
     ![](../core/media/psadapter-50-ps-configsecurity4.gif "PSAdapter_50_PS_ConfigSecurity4")  
  
6.  按一下**元件介面** 索引標籤。  
  
7.  按一下 + （加號） 新增至新的資料列**元件介面**清單。  
  
     此時就會顯示您可以在其中輸入元件介面名稱的欄位。  
  
     ![](../core/media/psadapter-51-ps-configsecurity5.gif "PSAdapter_51_PS_ConfigSecurity5")  
  
8.  輸入元件介面名稱，然後按一下**編輯**。  
  
     這則範例會使用元件介面 AR_ITEM_AGENT。  
  
     ![](../core/media/psadapter-52-ps-configsecurity6.gif "PSAdapter_52_PS_ConfigSecurity6")  
  
9. 在清單中，選取所需的存取層級，每個方法，然後按一下 **確定**。  
  
     此時就會顯示下列視窗。  
  
     ![](../core/media/psadapter-53-ps-configsecurity7.gif "PSAdapter_53_PS_ConfigSecurity7")  
  
10. 在右窗格中，向下捲動，然後按一下 **儲存**。  
  
## <a name="see-also"></a>另請參閱  
 [附錄 a： 元件介面方法](../core/appendix-a-component-interface-methods.md)   
 [附錄 c： 使用元件介面](../core/appendix-c-using-component-interfaces.md)