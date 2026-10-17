// Vercel Serverless Function: 決済金額をサーバー側で決めて PaymentIntent を作成する
// 環境変数 STRIPE_SECRET_KEY（sk_test_… / 本番は sk_live_…）を Vercel に設定してください。
const Stripe = require('stripe');

const stripe = new Stripe(process.env.STRIPE_SECRET_KEY);

// 金額はサーバー側で定義します（ブラウザからの金額は使いません）
const PLANS = {
  '30':  { amount: 16500, name: '30分撮影コース' },
  '60':  { amount: 29800, name: '60分撮影コース' },
  '120': { amount: 38500, name: '120分撮影コース' }
};

module.exports = async (req, res) => {
  if (req.method !== 'POST') {
    return res.status(405).json({ error: 'Method not allowed' });
  }

  const { plan, name, email, phone } = req.body || {};
  const p = PLANS[plan];

  if (!p) {
    return res.status(400).json({ error: 'Invalid plan' });
  }
  if (!name || !email || !phone) {
    return res.status(400).json({ error: 'Missing contact details' });
  }

  try {
    const intent = await stripe.paymentIntents.create({
      amount: p.amount,
      currency: 'jpy',
      description: p.name,
      receipt_email: email,
      metadata: { plan, name, phone },
      automatic_payment_methods: { enabled: true }
    });
    return res.status(200).json({ clientSecret: intent.client_secret });
  } catch (err) {
    console.error(err);
    return res.status(500).json({ error: 'Payment initialization failed' });
  }
};
