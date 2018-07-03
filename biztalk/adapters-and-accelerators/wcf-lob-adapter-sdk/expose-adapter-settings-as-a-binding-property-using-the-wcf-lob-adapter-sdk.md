---
title: 公開配接器設定為使用 WCF LOB 配接器 SDK 的繫結屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59728113-917e-4bca-8e1a-609cd6558944
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a51833c9f1a27185654bf8f0ddaca0fdd8ac0b57
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002335"
---
# <a name="expose-adapter-settings-as-a-binding-property-using-the-wcf-lob-adapter-sdk"></a>公開配接器設定為使用 WCF LOB 配接器 SDK 的繫結屬性
[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]會使用設定的連接集區、 中繼資料快取和其他配接器行為的不同類別中定義的屬性。 本主題描述如何顯示這些屬性，以及在繫結屬性，為使配接器取用者可以透過組態檔設定它們。  
  
### <a name="to-surface-an-adapter-setting-as-an-adapter-binding-property"></a>若要顯示為配接器繫結屬性的配接器設定  
  
1. 啟動 Visual Studio，然後在**檔案**功能表上，指向**新增**，然後按一下**專案**。  
  
2. 選擇**WCF LOB 配接器**範本，然後提供其他配接器專案資訊。  
  
3. 逐步執行[!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)]。 當您進入**配接器屬性**頁面上，新增您想要公開 （expose） 所提供的繫結屬性**屬性名稱**，**資料類型**，和**預設值**，然後按一下**新增**以加入新的配接器屬性。  
  
4. 完成[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]。 您的專案應該包含精靈所提供的新檔案。  
  
5. 在 Visual Studio，在 方案總管中開啟的配接器衍生的類別。 比方說，如果配接器專案的名稱是"SampleAdapter 」，配接器衍生類別可在 「 SampleAdapter.cs"。  
  
6. 移除您想要取得和設定從配接器設定屬性的私用變數。 所產生的私用變數[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]。  
  
7. 請更新讀取/寫入，或將介面卡設定的值 get/set 方法。 下列範例會使用配接器屬性，以便啟用效能計數器。  
  
   ```  
   [System.Configuration.ConfigurationProperty("enablePerfCounters", DefaultValue = false)]  
   public bool EnablePerfCounters  
   {  
       get { return environmentSettings.PerformanceCounters.Enabled;    }  
       set { environmentSettings.PerformanceCounters.Enabled = value; }  
   }  
   ```  
  
8. 在 Visual Studio 中，在**檔案**功能表上，按一下**全部儲存**。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 1： 開發 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)[開發活動](../../esb-toolkit/development-activities.md)