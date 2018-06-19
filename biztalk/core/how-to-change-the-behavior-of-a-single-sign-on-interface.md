---
title: 如何變更單一登入介面的行為 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4a4946a-e345-4c7e-835d-a3f7f72ebaca
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a4bedc387b879d5ddf21197e3dec4470f2e9b36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247854"
---
# <a name="how-to-change-the-behavior-of-a-single-sign-on-interface"></a>如何變更單一登入介面的行為
「企業單一登入」(SSO) 物件模型中的許多物件都會公開 IPropertyBag 介面，此介面可讓您修改指定物件的行為。 如果在 SSO 物件上呼叫 QueryInterface，則可以擷取 IPropertyBag 介面，並將其用來變更目前物件的行為。  
  
### <a name="to-change-the-behavior-for-a-specified-sso-interface"></a>變更指定 SSO 介面的行為  
  
1.  在指定的介面上使用 QueryInterface 來擷取 IPropertyBag 執行個體。  
  
2.  使用 IPropertyBag.Write 來設定介面的屬性、類型及值。  
  
     下表說明 IPropertyBag propName 和 ptrVar 參數的有效值。  
  
|propName|類型|ptrValue|可用於|  
|--------------|----------|--------------|---------------|  
|CurrentSSOServer|VT_BSTR|要將資訊傳送至的伺服器的名稱|全部|  
|Transaction|VT_UNKNOWN<br /><br /> VT_EMPTY|DTC ITransaction 指標，或 NULL 以清除範圍。|ISSOConfigStore::SetConfigInfo<br />ISSOConfigStore::GetConfigInfo <br />ISSOConfigStore::DeleteConfigInfo<br /><br /> ISSOAdmin::CreateApplication<br />ISSOAdmin::DeleteApplication <br />ISSOAdmin::UpdateApplication<br />ISSOAdmin::CreateFieldInfo<br /><br /> ISSOMapper::GetFieldInfo|  
|AppFilterFlags|VT_I4<br /><br /> VT_UI4|控制要篩選之應用程式的旗標。|ISSOMapper::GetApplications<br /><br /> ISSOMapper2::GetApplications2|  
|AppFilterFlagsMask|VT_I4<br /><br /> VT_UI4|控制要篩選之應用程式的旗標遮罩。|ISSOMapper::GetApplications<br /><br /> ISSOMapper2::GetApplications2|  
|AsyncCall|VT_BOOL|若為 True，則使用非同步 RPC 進行呼叫；若為 False，則使用同步 RPC。|ISSOConfigOM::GetServerStatus<br /><br /> ISSOAdmin::GetGlobalInfo|  
  
-   **CurrentSSOServer**： 判斷將 SSO 資訊傳送至伺服器，如下所示為標準的行為：  
  
    1.  在目前使用者的登錄中尋找。 可以使用命令列工具或 GUI，為目前的使用者設定伺服器名稱。  
  
    2.  在所有使用者的登錄中尋找。 可以使用命令列工具或 GUI，為所有的使用者設定伺服器名稱。  
  
    3.  如果在登錄中找不到 SSO 伺服器名稱，則使用目前的電腦。  
  
     將 CurrentSSOServer 設定為指定的伺服器會覆寫前述的指定介面程序。 一旦設定 CurrentSSOServer 之後，所有後續在該介面上的方法呼叫都會傳送到指定的伺服器。  
  
-   **交易**： 指定 DTC 交易的範圍內執行的作業由 SSO 物件模型。 您必須在 `ptrValue` 中傳遞 DTC ITransaction 指標，或 "null" 以清除目前的交易範圍。  
  
-   **AppFilterFlags/AppFilterMask**： 控制項類型的應用程式將會從 ISSOMapper.GetApplications 和 ISSOMapper2.GetApplications 所傳回。 如果應用程式旗標符合篩選器旗標和篩選器旗標遮罩所指定的旗標，它們就會傳回。 一種執行應用程式篩選的方式，是將 AppFilterFlagsMask 設定為 SSO_FLAG_APP_FILTER_BY_TYPE，然後再將 AppFilterFlags 設定為下列的一或多個項目：  
  
     SSO_APP_TYPE_INDIVIDUAL  
  
     SSO_APP_TYPE_GROUP  
  
     SSO_APP_TYPE_CONFIG_STORE  
  
     SSO_APP_TYPE_HOST_GROUP  
  
     SSO_APP_TYPE_PS_ADAPTER  
  
     SSO_APP_TYPE_PS_GROUP_ADAPTER  
  
-   **AsyncCall**： 如果為 true，則 SSO 會執行使用非同步遠端程序呼叫 (RPC) 的方法。 此方法在進行時會傳回 E_PENDING。 任何其他的傳回值都代表方法已完成。 AsyncCall 也可讓您輪詢完成的方法。