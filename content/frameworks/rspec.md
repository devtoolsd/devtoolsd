---
name: RSpec
slug: rspec
language: ruby
description: Behaviour-driven development testing framework for Ruby — readable `describe/it/expect` DSL and the standard for Rails testing.
website: https://rspec.info
github: rspec/rspec
year: 2005
pricing: free
open_source: true
license: MIT
tool_type: testing
tags: [testing, ruby, bdd, rails, unit-testing, integration-testing]
related_frameworks: [minitest]
features:
  - "Readable BDD DSL — `describe`, `context`, `it`, `expect` form a specification"
  - "`let` and `subject` for lazy-evaluated, DRY test data"
  - "Shared examples for reusing test cases across multiple classes"
  - "Custom matchers — extend `expect` with domain-specific matchers"
  - "Focused and pending tests with `fdescribe`, `fit`, `xdescribe`"
  - "Mocking and stubbing via `rspec-mocks` — `allow`, `expect`, `double`"
  - "Integration with Rails via `rspec-rails`"
  - "Works with FactoryBot and Capybara for complete test coverage"
install:
  gem: "gem install rspec"
  bundler: "bundle add rspec-rails --group test"
---

RSpec's `describe`, `context`, and `it` blocks produce test output that reads like a specification. Combined with FactoryBot for test data and Capybara for integration testing, RSpec forms the standard Rails test stack. Its shared examples, custom matchers, and `let`/`subject` helpers enable DRY, expressive test suites.

## Quick start

```bash
# For a Rails project
bundle add rspec-rails factory_bot_rails capybara --group test
rails generate rspec:install
```

```ruby
# spec/models/post_spec.rb
require 'rails_helper'

RSpec.describe Post, type: :model do
  subject(:post) { build(:post) }

  describe 'validations' do
    it { is_expected.to validate_presence_of(:title) }
    it { is_expected.to validate_length_of(:title).is_at_least(3) }
    it { is_expected.to belong_to(:author) }
  end

  describe '#published?' do
    context 'when published_at is set' do
      let(:post) { build(:post, published_at: 1.day.ago) }
      it { is_expected.to be_published }
    end

    context 'when published_at is nil' do
      let(:post) { build(:post, published_at: nil) }
      it { is_expected.not_to be_published }
    end
  end
end
```

```ruby
# spec/requests/posts_spec.rb
require 'rails_helper'

RSpec.describe 'Posts API', type: :request do
  let(:user) { create(:user) }
  let(:headers) { auth_headers(user) }

  describe 'GET /api/posts' do
    before { create_list(:post, 3, author: user) }

    it 'returns all posts' do
      get '/api/posts', headers: headers
      expect(response).to have_http_status(:ok)
      expect(json['data'].length).to eq(3)
    end
  end
end
```

## When to use

RSpec is the standard for Ruby and Rails projects — most Rails codebases use it. Its BDD style produces tests that serve as living documentation. Minitest is a lighter alternative built into Ruby's standard library, preferred by some teams for simplicity. For new Rails projects, RSpec + FactoryBot + Capybara is the proven stack. If you're greenfielding a non-Rails Ruby project, Minitest's simpler setup may be preferable.
